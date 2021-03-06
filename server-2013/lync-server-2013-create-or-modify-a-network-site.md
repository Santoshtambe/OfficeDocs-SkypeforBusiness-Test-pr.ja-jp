﻿---
title: 'Lync Server 2013: ネットワーク サイトの作成または変更'
TOCTitle: ネットワーク サイトの作成または変更
ms:assetid: 14e24856-9996-4da4-9f31-300940bdf5aa
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg398218(v=OCS.15)
ms:contentKeyID: 48271354
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 でのネットワーク サイトの作成または変更

 

_**トピックの最終更新日:** 2013-02-24_

通話受付管理 (CAC)、E9-1-1、およびメディア バイパスの展開は、*ネットワーク サイト*の構成に依存します。ネットワーク サイトは、ネットワーク地域内部で定義され、常に、ネットワーク地域に関連付けられます。ネットワーク サイトは、ブランチ オフィスの位置、建物の集合、またはキャンパスを表します。ネットワーク サイトは、帯域幅が同レベルのサブネットの集合を意味します。

ネットワーク サイトを作成または変更するには、以下の手順を使用します。 たとえば、1 つの音声機能について既にネットワーク サイトを作成している場合は、新しいネットワーク サイトを作成する必要はありません。他の音声機能も既存の同じサイトを使用します。 ただし、既存のネットワーク サイトの定義を変更して機能固有の設定を適用しなければならない場合があります。 たとえば、E9-1-1 用のネットワーク サイトを作成している場合、通話受付管理の展開時にネットワーク サイトを変更して、帯域幅ポリシー プロファイルを適用する必要があります。

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>機能固有の設定が存在する場合、機能ごとに「展開」のドキュメントに記載されている高度な音声機能に関連するネットワーク サイトの具体的な例と要件については、次を参照してください。
<ul>
<li><p><a href="lync-server-2013-configure-network-sites-for-cac.md">Lync Server 2013 での CAC のネットワーク サイトの構成</a></p></li>
</ul></td>
</tr>
</tbody>
</table>


ネットワーク サイトの操作の詳細については、「Lync Server 管理シェル」のドキュメントに記載されている次のコマンドレットを参照してください。

  - [New-CsNetworkSite](new-csnetworksite.md)

  - [Get-CsNetworkSite](get-csnetworksite.md)

  - [Set-CsNetworkSite](set-csnetworksite.md)

  - [Remove-CsNetworkSite](remove-csnetworksite.md)

## ネットワーク サイトの作成

通話受付管理、E9-1-1、またはメディア バイパスで使用できるネットワーク地域を作成します。

## 管理シェルを使用して、ネットワーク サイトを作成するには

1.  Lync Server 管理シェルを以下の手順で起動します。\[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Server 管理シェル**\] の順にクリックします。

2.  New-CsNetworkSite コマンドレットを実行して、ネットワーク サイトを作成します。
    
        New-CsNetworkSite -NetworkSiteID <string>
    
    次に例を示します。
    
        New-CsNetworkSite -NetworkSiteID Chicago -Description "Corporate headquarters"-NetworkRegionID NorthAmerica
    
    この例では、"NorthAmerica" ネットワーク地域に "Chicago" という名前のネットワーク サイトが作成されました。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>このコマンドを正常に実行するには、NorthAmerica ネットワーク地域があらかじめ存在する必要があります。</td>
    </tr>
    </tbody>
    </table>


3.  トポロジのネットワーク サイトを作成するには、他のサイトの設定に関してステップ 2 を繰り返します。

## Lync Server コントロール パネルを使用して、ネットワーク サイトを作成するには

1.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

2.  左側のナビゲーション バーで \[**ネットワーク構成**\] をクリックします。

3.  \[**サイト**\] ナビゲーション ボタンをクリックします。

4.  \[**新規**\] をクリックします。

5.  \[**新しいサイト**\] ページで、\[**名前**\] をクリックしてネットワーク サイトの名前を入力します。

6.  \[**地域**\] をクリックして、リストで地域をクリックします。

7.  オプションで、\[**帯域幅ポリシー**\] をクリックして、リストで帯域幅ポリシーをクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>帯域幅ポリシーが必要なのは、サイトで通話受付管理を展開する場合だけです。</td>
    </tr>
    </tbody>
    </table>


8.  オプションで、\[**場所のポリシー**\] をクリックして、リストで場所のポリシーをクリックします。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>場所のポリシーが必要なのは、サイトで E9-1-1 を展開する場合だけです。</td>
    </tr>
    </tbody>
    </table>


9.  オプションで、\[**説明**\] をクリックして、このネットワーク サイトを説明する追加情報を入力します。

10. \[**確定**\] をクリックします。

11. 他のサイトについての設定に関してステップ 4 ～ 10 を繰り返し、ご使用のトポロジのネットワーク サイトの作成を完了します。

## ネットワーク サイトの変更

通話受付管理、E9-1-1、またはメディア バイパスで使用できるネットワーク地域を変更します。

## ネットワーク サイトを変更するには

1.  Lync Server 管理シェルを以下の手順で起動します。\[**スタート**\]、\[**すべてのプログラム**\]、\[**Microsoft Lync Server 2013**\]、\[**Lync Server 管理シェル**\] の順にクリックします。

2.  Set-CsNetworkSite コマンドレットを実行して、ネットワーク サイトを変更します。
    
        Set-CsNetworkSite -Identity <string>
    
    次に例を示します。
    
        Set-CsNetworkSite -Identity Albuquerque -NetworkRegionID NorthAmerica
    
    この例では、"Albuquerque" という名前のサイトが "NorthAmerica" ネットワーク地域に移動されます。 ネットワーク サイトの構成を変更して、通話受付管理、E9-1-1、またはメディア バイパスを展開するには、Set-CsNetworkSite コマンドレットをそれぞれ BWPolicyProfileID または LocationPolicy パラメーターと組み合わせて実行し、ネットワーク サイトの設定を変更します。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>メディア バイパス用に BypassID パラメーターが用意されていますが、自動生成されるバイパス ID を無効にしないことを強くお勧めします。 メディア バイパス用にネットワーク サイトを構成するために、追加パラメーターを指定する必要はありません。</td>
    </tr>
    </tbody>
    </table>


3.  他のサイトについての設定に関してステップ 2 を繰り返し、ご使用のトポロジのネットワーク サイトの変更を完了します。

## Lync Server コントロール パネルを使用して、ネットワーク サイトを変更するには

1.  ブラウザー ウィンドウを開いて管理 URL を入力し、Lync Server コントロール パネルを開きます。Lync Server コントロール パネルを開くために使用できる他の方法の詳細については、「[Lync Server 2013 管理ツールを開く](lync-server-2013-open-lync-server-administrative-tools.md)」を参照してください。

2.  左側のナビゲーション バーで \[**ネットワーク構成**\] をクリックします。

3.  \[**サイト**\] ナビゲーション ボタンをクリックします。

4.  表内で、変更するネットワーク サイトをクリックします。

5.  \[**編集**\] をクリックして、\[**詳細の表示...**\] をクリックします。

6.  \[**サイトの編集**\] ページで、このネットワーク サイトの設定値を必要に応じて変更します。

7.  \[**確定**\] をクリックします。

8.  他のサイトについての設定に関してステップ 4 ～ 7 を繰り返し、ネットワーク サイトの変更を完了します。

