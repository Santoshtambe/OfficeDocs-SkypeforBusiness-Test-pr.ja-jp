﻿---
title: グループ通話ピックアップの処理能力の計画
TOCTitle: グループ通話ピックアップの処理能力の計画
ms:assetid: 0d654a19-6cf0-4118-903d-ec2c4e519253
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/JJ984297(v=OCS.15)
ms:contentKeyID: 52056535
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# グループ通話ピックアップの処理能力の計画

 

_**トピックの最終更新日:** 2015-03-09_

次の表は、処理能力の計画要件の土台として使用できる、グループ通話ピックアップのユーザー モデルを示しています。


> [!IMPORTANT]
> グループ通話ピックアップはコール パーク アプリケーションに基づきます。障害復旧に関する処理能力の計画では、ペアになったプールの各プールが、グループ通話ピックアップを含め、双方のプール内のコール パークサービスの負荷を処理できる必要があります。



### グループ通話ピックアップのユーザー モデル

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>指標</th>
<th>フロント エンド プールごと (8 つのフロントエンド サーバー)</th>
<th>Standard Edition サーバーごと</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>グループあたりの推奨ユーザー数</p></td>
<td><p>50</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>推奨グループ数</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>プールあたりの、グループ通話ピックアップが可能な最大ユーザー数</p></td>
<td><p>25,000</p></td>
<td><p>3,000</p></td>
</tr>
<tr class="even">
<td><p>プールおよび分あたりの、グループ通話ピックアップが可能な総ユーザー数に対する着信通話数の最大比率</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>プールおよび分あたりの、グループ通話ピックアップによって取得される通話数の最大比率</p></td>
<td><p>200</p></td>
<td><p>25</p></td>
</tr>
</tbody>
</table>


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
<td><ul>
<li><p>フロント エンド サーバーの数が 8 台に満たないフロント エンド プールでは、指標を直性的に計算します。たとえば、フロント エンド プールに 1 台のフロント エンド サーバーが含まれる場合、最大負荷は表の値の 1/8 として計算されます。</p></li>
<li><p>グループあたりの推奨ユーザー数とグループ数は、プールあたりの最大ユーザー数を超えない限り増減できます。たとえば、Standard Edition サーバーに 120 グループを含め、グループごとに 25 ユーザーを含めることができます。グループ通話ピックアップが可能なユーザーの数が依然としてユーザー モデルの最大数に収まっているためです (グループ通話ピックアップが可能なユーザー: 120 グループ * 25 ユーザー = 3,000 ユーザー)。</p></li>
</ul></td>
</tr>
</tbody>
</table>

