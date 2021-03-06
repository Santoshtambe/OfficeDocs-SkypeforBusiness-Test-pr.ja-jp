﻿---
title: フェデレーション ルートとメディア トラフィックの構成
TOCTitle: フェデレーション ルートとメディア トラフィックの構成
ms:assetid: 8b2f5f81-a955-4ad1-ad74-397322ff9521
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ688121(v=OCS.15)
ms:contentKeyID: 49887037
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# フェデレーション ルートとメディア トラフィックの構成

 

_**トピックの最終更新日:** 2012-10-15_

フェデレーションとは、別々の組織のユーザーがネットワーク境界を越えて通信することを許可する、複数の SIP ドメイン間での信頼関係のことです。 Lync Server 2013 パイロット プールに移行した後は、 Lync Server 2010 エッジ サーバーのフェデレーション ルートから Lync Server 2013 エッジ サーバーのフェデレーション ルートに移行する必要があります。

単一のサイト展開の場合、以下で説明する手順を使用して、フェデレーション ルートとメディア トラフィック ルートを Lync Server 2010 エッジ サーバーおよびディレクターから Lync Server 2013 エッジ サーバーに移行してください。


> [!IMPORTANT]
> フェデレーション ルートとメディア トラフィック ルートを変更するには、 Lync Server 2013 および Lync Server 2010 エッジ サーバーの保守作業を行うためのダウンタイムを計画する必要があります。また、この移行プロセスで機能が停止している間は、フェデレーション アクセスも使用できません。ダウンタイムは、ユーザー アクティビティが最も少ない時間帯に予定してください。また、ダウンタイムが発生することをエンド ユーザーに知らせる必要もあります。組織の事情に応じて停止を計画し、適切に対応してください。




> [!IMPORTANT]
> 従来の Lync Server 2010 エッジ サーバーが、アクセス エッジ サービス、Web 電話会議エッジ サービス、および音声ビデオ エッジ サービスに同じ FQDN を使用するように構成されている場合は、このセクションの手順はサポートされません。従来のエッジ サービスが同じ FQDN を使用するように構成されている場合は、まず、すべてのユーザーを Lync Server 2010 から Lync Server 2013 に移行します。次に、 Lync Server 2010 エッジ サーバーを使用停止にし、その後で、 Lync Server 2013 エッジ サーバーのフェデレーションを有効にします。




> [!IMPORTANT]
> XMPP フェデレーションが Lync Server 2013 エッジ サーバー経由でルーティングされる場合は、すべてのユーザーが Lync Server 2013 に移行され、XMPP のポリシーと証明書が構成され、XMPP フェデレーション パートナーが Lync Server 2013 で構成され、そして DNS エントリが更新されるまで、従来の Lync Server 2010 のユーザーは XMPP フェデレーション パートナーと通信できなくなります。



## Lync Server 2013 サイトから従来のフェデレーション関連付けを削除するには

1.  Lync Server 2013 フロントエンド サーバーで、トポロジ ビルダーに既存のトポロジを開きます。

2.  左ウィンドウで、 **Lync Server** のすぐ下にあるサイト ノードに移動します。

3.  サイトを右クリックし、\[**プロパティの編集**\] をクリックします。

4.  左ウィンドウで、\[**フェデレーション ルート**\] をクリックします。

5.  \[**サイトのフェデレーション ルートの割り当て**\] で、\[**SIP フェデレーションの有効化**\] チェック ボックスをオフにして、従来の Lync Server 2010 環境を経由したフェデレーション ルートを無効にします。
    
    ![\[プロパティの編集\] ダイアログ ボックス、\[フェデレーション ルート\] ページ](images/JJ688121.8d755ae0-fc7d-4253-b0db-0cf31b863c55(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、[フェデレーション ルート] ページ")

6.  \[**OK**\] をクリックして、\[プロパティの編集\] ページを閉じます。

7.  \[**トポロジ ビルダー**\] で、最上位ノードの \[**Lync Server**\] を選択します。

8.  \[**アクション**\] メニューの \[**トポロジの公開**\] をクリックします。

9.  \[**次へ**\] をクリックして公開プロセスを完了し、公開プロセスが完了したら、\[**完了**\] をクリックします。

## 従来のエッジ サーバーをフェデレーションされていないエッジ サーバーとして構成するには

1.  左ウィンドウで、\[**Lync Server 2010**\] ノード、\[**エッジ プール**\] ノードの順に移動します。

2.  エッジ サーバーを右クリックし、\[**プロパティの編集**\] をクリックします。

3.  左ウィンドウの \[**全般**\] を選択します。

4.  \[**このエッジ プールのフェデレーションの有効化 (ポート 5061)**\] チェック ボックス エントリをオフにし、\[**OK**\] をクリックしてページを閉じます。
    
    ![\[プロパティの編集\]、\[全般\]、フェデレーションの有効化をクリアする](images/JJ688121.3be2c8c0-9ed9-4544-bafd-b7694271fafc(OCS.15).jpg "[プロパティの編集]、[全般]、フェデレーションの有効化をクリアする")

5.  \[**操作**\] メニューで \[**トポロジの公開**\] を選択し、\[**次へ**\] をクリックします。

6.  **公開ウィザード**の実行が完了したら、\[**完了**\] をクリックしてウィザードを閉じます。

7.  従来のエッジ サーバーのフェデレーションが無効になっていることを確認します。
    
    ![トポロジ ビルダー、エッジ プール、無効化されたフェデレーション](images/JJ688121.a2948438-d51a-4aeb-9eaa-d899ca950758(OCS.15).jpg "トポロジ ビルダー、エッジ プール、無効化されたフェデレーション")

## Lync Server 2010 エッジ サーバーで証明書を構成するには

1.  従来の Lync Server 2010 エッジ サーバーから、アクセス プロキシの外部証明書と秘密キーをエクスポートします。

2.  Lync Server 2013 エッジ サーバーに、前の手順でエクスポートした、アクセス プロキシの外部証明書をインポートします。

3.  アクセス プロキシの外部証明書を、エッジ サーバーの Lync Server 2013 外部インターフェイスに割り当てます。

4.  Lync Server 2013 エッジ サーバーの内部インターフェイス証明書は、信頼された CA に要求して割り当てる必要があります。

## Lync Server 2013 エッジ サーバーを使用するように Lync Server 2010 のフェデレーション ルートを変更するには

1.  トポロジ ビルダーの左ウィンドウで、\[**Lync Server 2013**\] ノード、\[**エッジ プール**\] ノードの順に移動します。

2.  エッジ サーバーを右クリックし、\[**プロパティの編集**\] をクリックします。

3.  左ウィンドウの \[**全般**\] を選択します。

4.  \[**このエッジ プールのフェデレーションの有効化 (ポート 5061)**\] のチェック ボックス エントリをオンにし、\[**OK**\] をクリックしてページを閉じます。
    
    ![\[プロパティの編集\] ダイアログ ボックス、\[全般\] ページ](images/JJ688121.cc79a88c-cce4-4cab-80ad-4f70325dc7c4(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、[全般] ページ")

5.  \[**操作**\] メニューで \[**トポロジの公開**\] を選択し、\[**次へ**\] をクリックします。

6.  **公開ウィザード**の実行が完了したら、\[**完了**\] をクリックしてウィザードを閉じます。

7.  \[**フェデレーション (ポート 5061)**\] が \[**有効**\] に設定されていることを確認します。
    
    ![トポロジ ビルダー、エッジ プール、有効化されたフェデレーション](images/JJ688121.e8ccdada-23f4-47e5-a99d-5bf795fefc48(OCS.15).jpg "トポロジ ビルダー、エッジ プール、有効化されたフェデレーション")

## Lync Server 2013 エッジ サーバーのフェデレーションの次ホップを更新するには

1.  トポロジ ビルダーの左ウィンドウで、\[**Lync Server 2013**\] ノード、\[**エッジ プール**\] ノードの順に移動します。

2.  ノードを展開し、一覧内のエッジ サーバーを右クリックし、\[**プロパティの編集**\] をクリックします。

3.  \[**全般**\] ページの \[**次ホップの選択**\] で、ドロップダウン リストから Lync Server 2013 プールを選択します。
    
    ![\[プロパティの編集\] ダイアログ ボックス、\[次のホップ\] ページ](images/JJ688121.5741b9a8-e729-4457-9f62-38f08a2c5b02(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、[次のホップ] ページ")

4.  \[**OK**\] をクリックして、\[プロパティの編集\] ページを閉じます。

5.  \[**トポロジ ビルダー**\] で、最上位ノードの \[**Lync Server**\] を選択します。

6.  \[**操作**\] メニューの \[**トポロジの公開**\] をクリックし、ウィザードを完了します。

## Lync Server 2013 エッジ サーバーの送信メディア パスを構成するには

1.  \[トポロジ ビルダー\] の左ウィンドウで、\[**Lync Server 2013**\] ノードに移動してから、\[**Standard Edition フロントエンド サーバー**\] または \[**Enterprise Edition フロントエンド プール**\] に移動します。

2.  プールを右クリックし、\[**プロパティの編集**\] をクリックします。

3.  \[**関連付け**\] セクションで、\[**エッジ プールの関連付け (メディア コンポーネント用)**\] チェック ボックスをオンにします。
    
    ![\[プロパティの編集\] ダイアログ ボックス、\[全般\]、\[エッジ プールの関連付け\]](images/JJ688121.fd9b18ca-fda2-4764-9bf0-726bf39f6a12(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、[全般]、[エッジ プールの関連付け]")

4.  ボックスの一覧の \[Lync Server 2013 エッジ サーバー\] をクリックします。

5.  \[**OK**\] をクリックして、\[**プロパティの編集**\] ページを閉じます。

## Lync Server 2013 エッジ サーバーのフェデレーションを有効にするには

1.  トポロジ ビルダーの左ウィンドウで、\[**Lync Server 2013**\] ノード、\[**エッジ プール**\] ノードの順に移動します。

2.  ノードを展開し、一覧内の \[エッジ サーバー\] を右クリックし、\[**プロパティの編集**\] をクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>フェデレーションは、単一の エッジ プールに対してのみ有効にできます。複数のエッジ プールがある場合は、フェデレーション エッジ プールとして使用するエッジ プールを 1 つ選択します。</td>
    </tr>
    </tbody>
    </table>


3.  \[**全般**\] ページで、\[**このエッジ プールのフェデレーションの有効化 (ポート 5061)**\] 設定がオンになっていることを確認します。
    
    ![\[プロパティの編集\] ダイアログ ボックス、\[全般\] ページ](images/JJ688121.cc79a88c-cce4-4cab-80ad-4f70325dc7c4(OCS.15).jpg "[プロパティの編集] ダイアログ ボックス、[全般] ページ")

4.  \[**OK**\] をクリックして、\[プロパティの編集\] ページを閉じます。

5.  次に、サイト ノードに移動します。

6.  サイトを右クリックし、\[**プロパティの編集**\] をクリックします。

7.  左ウィンドウで、\[**フェデレーション ルート**\] をクリックします。

8.  \[**サイトのフェデレーション ルートの割り当て**\] で、\[**SIP フェデレーションの有効化**\] を選択し、ボックスの一覧の \[Lync Server 2013  エッジ サーバー\] をクリックします。
    
    ![\[プロパティの編集\]、\[フェデレーション ルート\] ページ](images/JJ688121.c50c13b8-0859-4e3e-8793-45c431a5b4b5(OCS.15).jpg "[プロパティの編集]、[フェデレーション ルート] ページ")

9.  \[**OK**\] をクリックして、\[**プロパティの編集**\] ページを閉じます。
    
    マルチサイト展開の場合は、この手順をサイトごとに実行します。

## エッジ サーバーの構成の変更を公開するには

1.  \[**トポロジ ビルダー**\] で、最上位ノードの \[**Lync Server**\] を選択します。

2.  \[**操作**\] メニューの \[**トポロジの公開**\] を選択し、ウィザードを完了します。

3.  展開内のすべてのプールに対して Active Directory のレプリケーションが発生するのを待ちます。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>次のメッセージが表示されることがあります。<br />
    <strong>警告: 複数のフェデレーション エッジ サーバーがトポロジに含まれています。この状態は、新しいバージョンの製品への移行中に発生することがあります。その場合、1 つのエッジ サーバーのみがフェデレーション用に実際に使用されます。外部 DNS SRV レコードが正しいエッジ サーバーを指していることを確認してください。複数のフェデレーション エッジ サーバーを (移行シナリオ以外で) 同時にアクティブにして展開する場合は、すべてのフェデレーション パートナーが Lync Server を使用していることを確認してください。また、外部 DNS SRV レコードにすべてのフェデレーション対応エッジ サーバーがリストされていることを確認してください。</strong><br />
    この警告は予期されるものであり、無視してもかまいません。</td>
    </tr>
    </tbody>
    </table>


## Lync Server 2013 エッジ サーバーを構成するには

1.  すべての Lync Server 2013 エッジ サーバーをオンラインにします。

2.  外部ファイアウォールのルーティング ルールまたはロード バランサー機器の設定を更新して、外部アクセス (通常は、ポート 443) およびフェデレーション (通常は、ポート 5061) の各 SIP トラフィックを、従来の エッジ サーバー ではなく、 Lync Server 2013  エッジ サーバー に送信します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>ハードウェア ロード バランサーがない場合は、フェデレーションの DNS A レコードを更新して、新しい Lync Server アクセス エッジ サーバーに解決する必要があります。混乱を最小限に抑えながらこれを実行するには、外部 Lync Server アクセス エッジ FQDN の TLL 値を減らして、DNS が新しい Lync Server アクセス エッジを指すように更新されたらフェデレーションとリモート アクセスが迅速に更新されるようにします。</td>
    </tr>
    </tbody>
    </table>


3.  次に、各 エッジ サーバー コンピューターの **Lync Server アクセス エッジ**を停止します。

4.  従来の各 エッジ サーバー コンピューターで、\[**管理ツール**\] から \[**サービス**\] アプレットを開きます。

5.  サービス リストで、\[**Lync Server アクセス エッジ**\] を見つけます。

6.  サービス名を右クリックし、\[**停止**\] を選択してサービスを停止します。

7.  スタートアップの種類を \[**無効**\] に設定します。

8.  \[**OK**\] をクリックして、\[**プロパティ**\] ウィンドウを閉じます。

