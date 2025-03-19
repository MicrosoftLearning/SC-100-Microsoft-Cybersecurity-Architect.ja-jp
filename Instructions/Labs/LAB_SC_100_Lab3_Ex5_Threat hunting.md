---
lab: 3
title: 演習 5 - 脅威ハンティング
---


# ラボ 3 - 演習 5 - コンテンツ検索 Microsoft Purview

あなたの会社は、その完全性とセキュリティに対する深刻な脅威に直面しています。 多数の悪意のあるメールが検出されました。 タスクは、これらのメールの送信者アドレスまたは件名行を識別することです。 これらの悪意のあるメールを特定したら、それらを一括で削除する必要があります。

## パート 1: ソリューションを設計する (必須)

### 設計アプローチ

最初の手順は、悪意のあるメールを特定することです。 したがって、現在のメール フローの分析が不可欠です。 Microsoft Defender ポータルでは、すべての送信および受信メール フローの包括的な概要と、このトラフィックを調査するためのその他の機能が提供されます。 修復アクションには、悪意のあるメールの削除が含まれます。 

### 提案されるソリューション

|要件|解決策|行動計画|
|----|----|----|
|悪意のあるメールを特定する|Microsoft Defender for Office 365|メール フローを調査し、メール ヘッダーを分析する|
|悪意のあるメールから発せられるリスクの排除|Microsoft Defender for Office 365|悪意のあるメールを削除する|

### タスク 1: 悪意のあるメールを調査する

Microsoft Defender ポータルで受信メールを調査し、疑わしいメールと悪意のあるコンテンツが含まれているメールを特定します。

1. 管理者アカウント **MOD 管理者**を使用して、Allan Deyoung として Microsoft Defender ポータル **https://security.microsoft.com** にサインインします。
1. Microsoft Security ポータルで、**[メールとコラボレーション]** を展開し、**[エクスプローラー]** を選択します。
1. **[エクスプローラー]** ページで、過去 30 日間のすべてのメール フローを表示するようにクエリの期間を調整し、**[更新]** を選択します。
1. 結果には、すべての受信メールと送信メールが表示されます。 メール フローとメールの件名を調査します。
1. "You have tasks due today" という件名のメールが疑わしいと表示されます。
1. さらに調査を行うには、対象を選択します。
1. 新しく表示された **[今日期限のタスクがあります]** ペイン ビューに情報が表示され、**[ビュー ヘッダー]** を選択します。
1. **[メール メッセージ ヘッダー]** ペインで、**[コピー メッセージ ヘッダー]** を選択し、**[Microsoft メール メッセージ ヘッダー]** を選択します。
1. ブラウザーで新しいタブが開きます。
1. **[メール メッセージ ヘッダー]** ページにメッセージ ヘッダーを貼り付け、**[ヘッダーの分析]** を選択します。
1. 結果を確認します。

Microsoft Defender ポータルでメール フローが正常に確認されました。

### タスク 2: 悪意のあるメールの一括削除を実行する

"You have tasks due today" という件名のメールはフィッシング攻撃であるという結論に達しました。 修復アクションには、PowerShell を使用してそれらのメールを一括削除する必要があります。

>[!NOTE] Exchange Online PowerShell モジュールが既にインストールされているはずです。 モジュールが見つからない場合は、モジュールをインストールする手順に従ってください。

1. マウスの右ボタンで Windows ボタンを選択して昇格された PowerShell ウィンドウを開き、 **[Windows PowerShell (管理者)]** を選択します。
1. **[ユーザー アカウント制御]** ウィンドウで、**[はい]** を選択して確定します。
1. 次のコマンドレットを入力して、Exchange Online PowerShell モジュールの最新版をインストールします。

    ```powershell
    Install-Module ExchangeOnlineManagement
    ```
1. 信頼されていないレポジトリ セキュリティ ダイアログで、[はい] を示す **[Y]** を選択して確定し、**Enter** キーを押します。  この処理は、完了までに時間がかかる場合があります。
1. マウスの右ボタンで Windows ボタンを選択して昇格された PowerShell ウィンドウを開き、 **[Windows PowerShell (管理者)]** を選択します。
1. **[ユーザー アカウント制御]** ウィンドウで、**[はい]** を選択して確定します。
1. 次のコマンドレットを入力して、Security & Compliance PowerShell に接続します。

    ```powershell
    Connect-IPPSSession
    ```

1. **[サインイン]** ウィンドウが表示されたら、admin@WWLxZZZZZZ.onmicrosoft.com としてサインインし (ZZZZZZ はラボ ホスティング プロバイダーから提供された一意のテナント ID)、テナントの管理パスワードを使用します。
1. 次のコマンドレットを入力してコンテンツ検索を実行し、コマンドレットで期間を指定します。

    ```powershell
    $Search=New-ComplianceSearch -Name "Purge phishing messages" -ExchangeLocation All -ContentMatchQuery '(Received:mm/dd/yyyy..mm/dd/yyyy) AND (Subject:"You have tasks due today")'
    Start-ComplianceSearch -Identity $Search.Identity
    ```
1. 次のコマンドレットを入力して、メッセージを物理的に削除します。

    ```powershell
    New-ComplianceSearchAction -SearchName "Purge phishing messages" -Purge -PurgeType HardDelete
    ---
You have successfully performed a mass-deletion of malicious mails.