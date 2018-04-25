﻿---
title: Lync Server 2013 の Standard Edition サーバー展開でのサーバーの併置
TOCTitle: Standard Edition サーバー展開でのサーバーの併置
ms:assetid: 0763ffab-4fd6-463a-8e62-d97876b376d3
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398131(v=OCS.15)
ms:contentKeyID: 48271166
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 の Standard Edition サーバー展開でのサーバーの併置

 

_**トピックの最終更新日:** 2013-01-20_

このセクションでは、Lync Server 2013 Standard Edition サーバー展開で併置できるサーバーの役割、データベース、およびファイル共有について説明します。

## サーバーの役割

Lync Server 2013 では、音声ビデオ会議サービス、仲介サービス、監視、およびアーカイブが Standard Edition サーバーに併置されますが、これらを有効にするには追加の構成が必要です。仲介サービスは、別のサーバー上に展開することもできます。

信頼されたアプリケーション サーバーは、Standard Edition サーバーと併置できます。

次のサーバーの役割は、それぞれ別のコンピューターに展開する必要があります。

  - ディレクター

  - エッジ サーバー

  - 仲介サーバー (Standard Edition サーバーと併置しない場合)

  - Office Web Apps サーバー

## データベース

既定では、SQL Server Express のバックエンド データベースは、Standard Edition サーバーに併置されます。 これを別個のコンピューターへ移動することはできません。1 つの例外を除き、Standard Edition サーバーにはそれ以外のデータベースを併置できません。常設チャット サーバーを Standard Edition サーバーに展開する場合は、常設チャット データベースと常設チャット コンプライアンス データベースを同じ Standard Edition サーバーに併置できます。

次のそれぞれのデータベースは、単一のデータベース サーバーに併置できます。

  - 監視データベース

  - アーカイブ データベース

  - Enterprise Edition フロントエンド プールのバックエンド データベース

これらのデータベースのいくつか、またはすべてを単一の SQL インスタンスに併置できます。また、これらの各データベースをそれぞれ別の SQL インスタンスで使用することもできます。ただし、この場合、次の制約があります。

  - 各 SQL インスタンスには、単一のバックエンド データベース (Enterprise Edition フロントエンド プールの場合)、単一の監視データベース、単一のアーカイブ データベース、単一の常設チャット データベース、および常設チャット コンプライアンス データベースのみを含めることができます。

  - データベース サーバーは、複数の Enterprise Edition フロントエンド プール、アーカイブを実行する複数のサーバー、監視を実行する複数のサーバー、複数の 常設チャット データベース、および複数の 常設チャット コンプライアンス データベースをサポートできません。しかし、データベースで同じ SQL Server インスタンスを使用しているか、個別の SQL Server インスタンスを使用されているかに関係なく、データベース サーバーは、フロントエンド プール、アーカイブ サーバー、監視サーバー、常設チャット データベース、および常設チャット コンプライアンス データベースをそれぞれ 1 つずつサポートできます。

このセクションで後述するように、ファイル共有をデータベースと併置できます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013 では、監視およびアーカイブ用ストレージと展開内の一部またはすべてのユーザーの Exchange 2013 ストレージを統合できます。Lync Server を実行するサーバーまたはコンポーネントを Exchange ストレージと同じサーバー上に展開することはできません。</td>
</tr>
</tbody>
</table>



> [!IMPORTANT]
> データベースの併置がサポートされていても、データベースのサイズはすぐに大きくなることがあります。たとえば、アーカイブ データベースと他のデータベースを併置することを考慮するときには、数名以上のユーザーのメッセージをアーカイブすると、アーカイブ データベースが必要とするディスク容量が非常に大きくなる可能性があることに注意してください。このため、複数のデータベース (特にアーカイブ データベース、常設チャット データベース、および 常設チャット コンプライアンス データベース) をエンタープライズ プールのバックエンド データベースと併置することはお勧めしません。



## ファイル共有

ファイル共有は、別個のサーバーを使用することも、次のいくつか、またはすべてと同じサーバーに併置することもできます。

  - データベース サーバー (Enterprise Edition フロントエンド プールのバック エンド サーバーを含む)

  - アーカイブ データベース

  - 監視データベース

  - 常設チャット データベース

  - 常設チャット コンプライアンス データベース

単一のファイル共有を複数のフロントエンド プール、および複数の Standard Edition サーバーで使用できます (これらのプールやサーバーはすべて同じサイトに存在)。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013 では、監視およびアーカイブは、Lync Server ファイル共有を Standard Edition サーバーとして使用します。</td>
</tr>
</tbody>
</table>


## その他のコンポーネント

リバース プロキシ サーバーは併置できません。リバース プロキシ サーバーは、Lync Server 2013 のコンポーネントではありませんが、Lync Server 2013 のサーバーの役割でフェデレーション ユーザーのために Web コンテンツの共有をサポートする場合に必要です。ただし、組織内で他のアプリケーションに使用している既存のリバース プロキシ サーバーにサポートを構成することによって、Lync Server 2013 展開にリバース プロキシのサポートを実装することはできます。

Exchange UM コンポーネントまたは SharePoint コンポーネントは、どの Lync Server 2013 の役割とも併置できません。
