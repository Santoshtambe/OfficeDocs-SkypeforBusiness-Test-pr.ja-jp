﻿---
title: 'Lync Server 2013: データベースのセキュリティ強化および保護'
TOCTitle: Lync Server 2013 のデータベースのセキュリティ強化および保護
ms:assetid: 6953e721-3511-4235-b848-51bab093dc89
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn518330(v=OCS.15)
ms:contentKeyID: 60498575
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 のデータベースのセキュリティ強化および保護

 

_**トピックの最終更新日:** 2016-12-08_

Microsoft Lync Server 2013 は、ユーザー情報、会議の状態、アーカイブ データ、および通話詳細記録 (CDR) を格納するために、SQL Server データベースも使用します。Lync Server バックエンド データベースに格納された Lync Server 2013 データの可用性を最大限に高めるには、フォールト トレランスが向上し、トラブルシューティングが容易になるように、アプリケーション データを分割します。アプリケーション データを分割する方法は、次のとおりです。

  - **サーバーの分割に関するベスト プラクティスを使用します。** オペレーティング システム、アプリケーション、およびプログラム ファイルをデータ ファイルと分離します。

  - **トランザクション ログ ファイルとデータベース ファイルを格納します。** これらのファイルを別々の場所に格納することにより、フォールト トレランスを向上させ、復旧処理を最適化します。これらのファイルは、暗号化されたディスクまたはボリュームに格納します。

  - **サーバーのクラスター化を使用します。** バックエンド サーバーをクラスター化し、Lync Server 2013 システムの可用性を高めます。

  - **すべてのデータ バックアップが暗号化され、正しく処理されていることを確認します。** バックアップ メディアの紛失、破棄、または誤った設置は、Lync Server 2013 展開のデータ セキュリティにとって重大な脅威となる可能性があります。

Standard Edition サーバー以外の Lync Server 2013 サーバーでは、SQL Server Express インスタンス (RTCLOCAL インスタンス) にはリモートからアクセスできません。また、Standard Edition サーバー上の SQL Server Express を除いて、ローカルのファイアウォール例外が作成されることはありません。Standard Edition サーバーでは、バックエンド データベースおよび中央管理ストア (CMS) が設定され、リモートからアクセスできます。SQL Server データベースのセキュリティを強化するには、次の操作を実行できます。

  - Standard Edition サーバー上の SQL Server Express ファイアウォールをカスタマイズして、データベースにリモートからアクセスできるサーバーのスコープを制限します。既定では、すべての IP アドレスがデータベースにリモートからアクセスできます。

  - SQL Server 構成マネージャーを使用して、SQL Server リモート アクセス用のプロトコル、IP アドレス、およびポートを指定します。
    
      - Lync Server 2013 では TCP/IP プロトコルを使用します。IP version 4 (IPv4) をサポートし、IP version 6 (IPv6) はサポートしません。
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Lync Server 2013 は、デュアル IP スタックが有効になっているネットワークで動作できます。</td>
        </tr>
        </tbody>
        </table>
    
      - Lync Server 2013 は複数の IP アドレス (マルチホーム ネットワーク アドレス カード) をサポートします。SQL Server が特定の IP アドレス (個別のアドレスまたはサブネット単位) のみをリッスンすることや、特定のプロトコルのみを使用することを指定できます。
    
      - Lync Server 2013 は静的および動的な SQL Server ポートをサポートします。

  - 既定でない静的ポートで SQL Server を実行し、SQL Server ブラウザーを実行しません (この結果、クライアントにリッスン ポートをレポートできません)。フロント エンド サーバー、監視サーバー、アーカイブ サーバー、管理コンソール (Lync Server 管理シェル、Lync Server コントロール パネル、またはトポロジ ビルダーを実行)、および Lync Server データベースを実行している他のすべてのサーバーを含めて、各 SQL Server クライアントでのカスタム構成が必要になります。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>データベースへのアクセスは、信頼できるデータベース管理者に制限する必要があります。悪意のあるデータベース管理者は、 Lync Server 2013 サーバーへの直接アクセスや制御が付与されていない場合でも、データベースにデータを挿入したりデータを変更したりして、 Lync Server 2013 サーバーの特権を取得したり、サービスの機密情報を入手する可能性があります。</td>
</tr>
</tbody>
</table>


カスタム構成および SQL Server データベースのセキュリティ強化の詳細については、NextHop のブログ記事「Using Lync Server 2010 with a Custom SQL Server Network Configuration (英語)」([http://go.microsoft.com/fwlink/p/?LinkId=214008](http://go.microsoft.com/fwlink/p/?linkid=214008)) を参照してください。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>オペレーティング システムとアプリケーション サーバーのセキュリティも強化できます。また、グループ ポリシーを使用して Lync Server 展開にセキュリティ ロックダウンを実装できます。詳細については、「 <a href="lync-server-2013-hardening-and-protecting-servers-and-applications.md">Lync Server 2013 のサーバーおよびアプリケーションの強化と保護</a>」を参照してください。</td>
</tr>
</tbody>
</table>

