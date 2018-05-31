﻿---
title: 'Lync Server 2013: リモート ユーザー アクセスの有効化または無効化'
TOCTitle: リモート ユーザー アクセスの有効化または無効化
ms:assetid: cd9d3ddc-4839-457a-86d9-b15413e74002
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg182586(v=OCS.15)
ms:contentKeyID: 48273601
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でのリモート ユーザー アクセスの有効化または無効化

 

_**トピックの最終更新日:** 2013-02-23_

リモート ユーザーは、組織内の永続的な Active Directory ID を持つ、組織内のユーザーです。リモート ユーザーは組織のネットワークに接続していない場合、仮想プライベート ネットワーク (VPN) を使用してネットワークの外から Lync Server にサインインすることがよくあります。リモート ユーザーには自宅や外出先で作業する従業員のほか、エンタープライズ資格情報を付与された信頼できるベンダーなどのリモート作業者が含まれます。リモート ユーザーのリモート ユーザー アクセスを有効にすると、サポートされるリモート ユーザーはインターネット経由で接続できるようになるので、 Lync Server を使用して内部ユーザーとコラボレーションを行うために VPN を使用して接続する必要がありません。

リモート ユーザー アクセスをサポートするには、リモート ユーザー アクセスを有効にする必要があります。有効にする場合は、組織全体に対して有効にします。後でリモート ユーザー アクセスを一時的または永久に禁止する場合は、組織に対するリモート ユーザー アクセスを無効にできます。組織に対するリモート ユーザー アクセスを有効または無効にするには、このセクションの手順を使用します。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>リモート ユーザー アクセスを有効にした時点では、アクセス エッジ サービスを実行するサーバーがリモート ユーザーとの通信をサポートするという指定が行われるだけです。リモート ユーザー アクセスの使用を管理するポリシーを少なくとも 1 つ構成するまで、リモート ユーザーは組織内のインスタント メッセージング (IM) や会議に参加できません。 あるポリシー レベルで適用されている Lync Server ポリシー設定が、他のポリシー レベルで適用されている設定によって無効になることがあります。Lync Server ポリシーの優先順位は、ユーザー ポリシーが最も高く、サイト ポリシー、グローバル ポリシー (優先度が最も低い) と続きます。つまり、ポリシー設定が、そのポリシーの影響を受けるオブジェクトに近いほど、オブジェクトに及ぼす影響は大きくなります。リモート ユーザー アクセスの使用に対するポリシーの構成については、「<a href="lync-server-2013-configure-policies-to-control-remote-user-access.md">Lync Server 2013 でのリモート ユーザー アクセスを制御するポリシーの構成</a>」を参照してください。</td>
</tr>
</tbody>
</table>


## 組織に対するリモート ユーザー アクセスを有効または無効にするには

1.  RTCUniversalServerAdmins グループ (または同等のユーザー権限を持つグループ) のメンバーであるユーザー アカウントまたは CsAdministrator の役割に割り当てられているユーザー アカウントから、内部展開の任意のコンピューターにログオンします。

2.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

3.  左側のナビゲーション バーで \[**フェデレーションと外部アクセス**\] をクリックし、\[**アクセス エッジ構成**\] をクリックします。

4.  \[**アクセス エッジ構成**\] ページで、\[**グローバル**\]、\[**編集**\]、\[**詳細の表示**\] の順にクリックします。

5.  \[**アクセス エッジ構成の編集**\] で、次のどちらかの操作を行います。
    
      - 組織に対してリモート ユーザー アクセスを有効にするには、\[**リモート ユーザー アクセスを有効にする**\] チェック ボックスをオンにします。
    
      - 組織に対してリモート ユーザー アクセスを無効にするには、\[**リモート ユーザー アクセスを有効にする**\] チェック ボックスをオフにします。

6.  \[**確定**\] をクリックします。

Lync Server を実行するサーバーへのリモート ユーザーのサインインを有効にするには、リモート ユーザー アクセスをサポートする外部アクセス ポリシーを少なくとも 1 つ構成する必要もあります。詳細については、「展開」または「操作」のドキュメントの「[Lync Server 2013 でのリモート ユーザー アクセスを制御するポリシーの構成](lync-server-2013-configure-policies-to-control-remote-user-access.md)」を参照してください。

## Windows PowerShell コマンドレットを使用してリモート ユーザー アクセスを有効または無効にする

Windows PowerShell および Set-CsAccessEdgeConfiguration コマンドレットを使用してリモート ユーザー アクセスを管理できます。このコマンドレットは、Lync Server 2013 管理シェルまたは Windows PowerShell のリモート セッションから実行できます。リモートの Windows PowerShell を使用して Lync Server に接続する方法の詳細については、Lync Server Windows PowerShell のブログ記事「Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell」 ([http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876)) を参照してください。

## リモート ユーザー アクセスを有効にするには

  - リモート ユーザー アクセスを有効にするには、 **AllowOutsideUsers** プロパティの値を True ($True) に設定します。
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $True

## リモート ユーザー アクセスを無効にするには

  - リモート ユーザー アクセスを無効にするには、 **AllowOutsideUsers** プロパティの値を False ($False) に設定します。
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $False
