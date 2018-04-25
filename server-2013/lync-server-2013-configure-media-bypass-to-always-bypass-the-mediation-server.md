﻿---
title: メディア バイパスを構成して仲介サーバーを常にバイパスする
TOCTitle: メディア バイパスを構成して仲介サーバーを常にバイパスする
ms:assetid: 370c4f54-e520-4d77-96a3-84c5e84a9996
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg425846(v=OCS.15)
ms:contentKeyID: 48271748
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# メディア バイパスを構成して仲介サーバーを常にバイパスする

 

_**トピックの最終更新日:** 2013-02-25_

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>このトピックは、メディアに仲介サーバーをバイパスさせたい特定のサイトまたはサービスのピア (公衆交換電話網 (PSTN) ゲートウェイ、IP-PBX、またはインターネット テレフォニー サービス プロバイダー (ITSP) のセッション ボーダー コントローラー (SBC)) へのすべてのトランク接続に、すでにメディア バイパスを構成したことを前提にしています。<br />
通話受付管理もまた有効である状態で、常に仲介サーバーをバイパスするようにメディアを構成することはできません。 これらの設定には互換性がなく、ゆえに Lync Server コントロール パネル ユーザー インターフェイスではこれらの設定を同時に行うことはできません。</td>
</tr>
</tbody>
</table>


仲介サーバーへのピアに関連付けられた個別のトランク接続に対してメディア バイパスを有効にするのに加え、メディア バイパスのグローバル設定もまた構成する必要があります。このトピックのステップに従ってメディア バイパスのグローバル設定を構成する場合、Lync エンドポイントおよびトランク接続のメディア バイパスを構成したすべてのピア間の接続が良好であるというのが前提です。

Lync Server エンドポイント、およびそれぞれのトランク接続がメディア バイパスに対して有効になっている仲介サーバーへのすべてのピア間の接続が良好ではない場合、メディア バイパスを使用する際にサイトおよび地域情報を使用することから、グローバル メディア バイパス設定を構成する必要があります。これにより、メディアが仲介サーバーをバイパスするか判定する際に、よりよく制御できます。これを行うには、「[サイトおよび地域情報を使用するためのメディア バイパス グローバル設定の構成](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md)」および「[Lync Server 2013 でのネットワーク サイトとサブネットの関連付け](lync-server-2013-associate-a-subnet-with-a-network-site.md)」のステップを参照してください。

## 仲介サーバーを常にバイパスするよう、メディア バイパスをグローバルに有効化するには

1.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

2.  左側のナビゲーション バーで \[**ネットワーク構成**\] をクリックします。

3.  リスト内の \[**グローバル**\] 構成をダブルクリックします。

4.  \[**グローバル設定の編集**\] ページの \[**メディア バイパスを有効にする**\] チェック ボックスをオンにします。

5.  \[**常にバイパスする**\] をクリックします。

6.  \[**確定**\] をクリックします。

## 関連項目

#### 概念

[Lync Server 2013 メディア バイパスの構成](lync-server-2013-configure-media-bypass.md)  
[Lync Server 2013 でのグローバル メディア バイパス オプション](lync-server-2013-global-media-bypass-options.md)  
[Lync Server 2013 のメディア バイパスと仲介サーバー](lync-server-2013-media-bypass-and-mediation-server.md)  

#### その他のリソース

[Lync Server 2013 でのメディア バイパスの計画](lync-server-2013-planning-for-media-bypass.md)
