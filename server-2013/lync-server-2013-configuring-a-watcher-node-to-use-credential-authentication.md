﻿---
title: 資格情報認証を使用する監視ノードの構成
TOCTitle: 資格情報認証を使用する監視ノードの構成
ms:assetid: 032e33f3-9483-42e6-a33c-347eb6779597
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ204632(v=OCS.15)
ms:contentKeyID: 48271098
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# 資格情報認証を使用する監視ノードの構成

 

_**トピックの最終更新日:** 2012-10-20_

ウォッチャー ノードのコンピューターが境界ネットワークの外側にある場合は、代理トランザクションを実行するようにウォッチャー ノードを構成するために、少し異なる手順に従う必要があります。具体的には、信頼されたアプリケーション プールや信頼されたアプリケーションを作成せずに、境界ネットワークの内側にあるコンピューターにウォッチャー ノードが通知を送信できるようにする証明書をインストールする必要があります。つまり、次に示す個別の 2 つのタスクを完了する必要があります。

  - コンピューターの RTC Local Read-only Administrators グループのメンバーシップを更新する

  - ウォッチャー ノード構成ファイルをインストールする

## RTC Local Read-Only Administrators グループのメンバーシップの更新

ウォッチャー ノードが境界ネットワークの外側にある場合は、Network Service アカウントをウォッチャー ノード コンピューターの RTC Local Read-only Administrators グループに追加する必要があります。そのためには、ウォッチャー ノードで以下の手順を完了します。

1.  \[**スタート**\] メニューの \[**コンピューター**\] を右クリックし、\[**管理**\] をクリックします。

2.  サーバー マネージャーで、\[**構成**\]、\[**ローカル ユーザーとグループ**\] の順に展開し、\[**グループ**\] をクリックします。

3.  \[グループ\] ウィンドウで、\[**RTC Local Read-only Administrators**\] をダブルクリックします。

4.  \[**RTC Local Read-only Administrators のプロパティ**\] ダイアログ ボックスで、\[**追加**\] をクリックします。

5.  \[**ユーザー、コンピューター、サービス アカウント、またはグループの選択**\] ダイアログで、\[**場所**\] をクリックします。

6.  \[**場所**\] ダイアログ ボックスで、ウォッチャー ノード コンピューターの名前を選択し、\[**OK**\] をクリックします。

7.  \[**選択するオブジェクト名を入力してください**\] ボックスに、「**Network Service**」と入力し、\[**OK**\] をクリックします。

8.  \[**RTC Local Read-only Administrators のプロパティ**\] ダイアログ ボックスで、\[**OK**\] をクリックし、\[**サーバー マネージャー**\] を閉じます。

ウォッチャー ノード コンピューターを再起動します。

## ウォッチャー ノード構成ファイルのインストール

ウォッチャー ノード コンピューターの再起動後、次の手順は Watchernode.msi ファイルの実行です。このファイルを実行するには、\[**スタート**\] メニュー、\[**すべてのプログラム**\]、\[**Lync Server 2013**\]、\[**Lync Server 管理シェル**\] の順にクリックして、Lync Server 2013 管理シェルを開きます。Lync Server 管理シェルで、次のコマンドを入力し、Enter キーを押します (必ず Watchernode.msi のコピーの実際のパスを指定してください)。

    C:\Tools\Watchernode.msi Authentication=Negotiate

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>前述のように、Watchernode.msi はコマンド ウィンドウから実行することもできます。コマンド ウィンドウを開くには、[<strong>スタート</strong>] メニューをクリックし、[<strong>コマンド プロンプト</strong>] を右クリックして、[<strong>管理者として実行</strong>] をクリックします。コマンド ウィンドウが開いたら、先ほどと同じコマンドを入力します。</td>
</tr>
</tbody>
</table>


ウォッチャー ノードを信頼されたアプリケーション プールとしてセットアップできない場合はいつでも、ネゴシエート モードが使用されます。このモードでは、管理者がウォッチャー ノードのテスト ユーザー パスワードを管理する必要があります。
