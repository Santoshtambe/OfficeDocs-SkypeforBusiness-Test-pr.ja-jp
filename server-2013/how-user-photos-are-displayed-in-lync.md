﻿---
title: Lync でユーザーの写真を表示する方法
TOCTitle: Lync でユーザーの写真を表示する方法
ms:assetid: b44a364d-a1d2-4d45-b27a-b5f77775e233
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Dn783119(v=OCS.15)
ms:contentKeyID: 62833687
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync でユーザーの写真を表示する方法

 

_**トピックの最終更新日:** 2016-12-08_

**概要:** Lync クライアントに表示されるユーザーの写真は、使用している Lync の機能によって異なることがあります (会議中や IM チャット中など)。

Lync 2010 では、他の Lync ユーザーに表示される自分の Lync プロファイルに写真を含めることができるようになりました。また、Lync クライアントで連絡先の写真を表示するかどうかも選択できます。Lync 2013 では、ユーザーの高解像度の写真もサポートされます。このトピックでは、Lync クライアントがユーザーの写真を取得して表示する方法、画像の保存場所、各画像ソースに関する制限事項、およびさまざまな Lync サービスでユーザーの写真を使用する方法について、説明します。

## 計画に関する考慮事項

ユーザーの写真のサポートを実装しようとしているときには、次のことを考慮する必要があります。

  - ユーザーの高解像度の写真をサポートするためには、そのユーザーのメールボックスが Exchange 2013 にあり、Lync ユーザー アカウントが Lync 2013 プールにある必要があります。

  - ユーザーの高解像度の写真は、Lync Server 2013 と Exchange 2013 の両方を使用する環境でのみサポートされます。

  - Exchange 2010 にメールボックスがあるユーザーは、自分のユーザーの写真のソースとして、AD DS の **thumbnailPhoto** 属性を常に使用します。

  - AD DS の **thumbnailPhoto** 属性として保存されたユーザーの写真は、外部連絡先/フェデレーション連絡先には表示されません。

  - ユーザーの連絡先の写真が AD DS に保存されている場合、使用される画像ファイルの上限は 96 × 96 ピクセルに、ファイルのサイズも 100 KB 以下に制限されます。

  - Lync Server と Exchange Server の間の接続が失われた場合は、AD DS の **thumbnailPhoto** (そのユーザーの低解像度の写真) が、内部ユーザーに対してのみ表示されます。

  - ユーザーの高解像度の写真は、Lync 2013 会議でアクティブな発言者がビデオを有効にしていない場合に表示されます。また、ギャラリーの写真のサムネイルにマウスを置くと、高解像度の写真が表示されます。

## Lync 2010 のユーザーの写真

Lync 2010 クライアントでは、プロファイルの写真の表示方法を \[**既定のコーポレート ピクチャ**\] と \[**Web アドレスからピクチャを表示する**\] の 2 つから選択できます。

## 既定のコーポレート ピクチャ

\[**既定のコーポレート ピクチャ**\] を選んだ場合、表示する写真は Lync によって Active Directory ドメイン サービス から取得されます。使用される画像は、Active Directory ドメイン サービス の **thumbnailPhoto** 属性の値として定義したものです。これは、Exchange によって Outlook に表示される画像のファイルと同じです。

Active Directory ドメイン サービス からの画像を使用するときには、次のような考慮事項があります。

  - サポートされる画像のピクセル数は最大 96 × 96 で、画像ファイルの最大サイズは 100 KB です。

  - 既定では、ユーザーは **thumbnailPhoto** 属性で使用される画像を変更できますが、Lync クライアントから直接には変更できません。また、Active Directory ドメイン サービス によってこの属性を無効にできます。

  - Active Directory ドメイン サービス に保存された画像は組織外の連絡先には表示されません (フェデレーション連絡先にも表示されません)。

  - 大規模な組織では、多数のユーザーが画像を保存したり取得したりすることで、Active Directory ドメイン サービス データベースのサイズおよびパフォーマンスに影響を与えることがあります。

  - 画像の大きさやファイル サイズが制限されているということは、低解像度の写真しか利用できないということです。

## ユーザーが Active Directory ドメイン サービス でユーザーの写真を管理する方法

ユーザーは、Lync 2010 クライアントから直接には Active Directory ドメイン サービス プロファイルの写真を変更できません。変更するには、次のいずれかの可能な方法を使用します。

  - **SharePoint Server**   ユーザーが写真を SharePoint Server の \[個人用サイト\] にアップロードして、[SharePoint のプロファイル同期を構成](http://go.microsoft.com/fwlink/p/?linkid=507466) すると、Active Directory ドメイン サービス の **thumbnailPhoto** 属性と写真を同期できます。

  - **一般アクセス可能な URL に保存した写真**   ユーザーは、自分の写真に、使用したい画像のための一般アクセス可能な URL を指定して構成できます。その画像には、誰でもパスワードなしでアクセスできる必要があります。指定した Web アドレスに保存されている画像が、プレゼンス情報の連絡先カード カテゴリを通じて他のユーザーに転送されます。Lync クライアントでユーザーの写真を表示する必要がある場合は、指定した Web アドレスからその画像が取得されます。

  - **Windows PowerShell の Exchange 2010 コマンドレット**   管理者は、Exchange 2010 管理シェルで [Import-RecipientDataProperty](http://go.microsoft.com/fwlink/p/?linkid=507468) コマンドレットを実行して、**thumbnailPhoto** 属性を管理できます。Exchange 2010 コマンドレットによって画像がインポートされると、そのファイル サイズは 10 KB に制限されます。

  - **サード パーティ製のツール**   ユーザーは、自分が所有する写真のみ、**thumbnailPhoto** 属性に対してアップロードできます。

## Web アドレスからピクチャを表示する

\[**Web アドレスからピクチャを表示する**\] を選んだ場合は、入力したアドレスから取得された画像が、Lync にユーザーの写真として表示されます。

Web アドレスからの画像を使用するときには、次のような考慮事項があります。

  - ファイル サイズの制限は、[New-CsClientPolicy](http://go.microsoft.com/fwlink/p/?linkid=507463) コマンドレットで定義したクライアント ポリシーの **MaxPhotoSizeKB** 属性で決定されます。既定ではサイズの上限は 30 KB で、最大値は 100 KB です。画像の解像度には制限がありませんが、サイズの上限を超える画像ファイルを使用しようとしても、Lync クライアントにダウンロードされません。この値を 0 に設定すると、すべてのユーザーの写真が Lync では使用できなくなります。

  - Web アドレスからのユーザーの写真が、外部 (フェデレーション) 連絡先にも表示されます。

## クライアント ポリシー コマンドレットによるユーザーの写真の管理

Lync Server 2010 では、クライアント ポリシーの設定は CsClientPolicy コマンドレットによって構成されます。構成されたポリシー設定は、インバンド プロビジョニングによってクライアントに送られます。ユーザーの写真に関するエクスペリエンスを決定する CsClientPolicy コマンドレットの 2 つのパラメーターは、**DisplayPhoto** と **MaxPhotoSizeKB** です。**DisplayPhoto** および **MaxPhotoSizeKB** に対応するインバンド プロビジョニング パラメーターは、**PhotoUsage** です。**PhotoUsage** パラメーターの値は、**endpointConfigurationprovisionGroup** を経由して送信されます。詳細については、「[クライアントのポリシーおよび設定の概要](http://go.microsoft.com/fwlink/?linkid=507470)」を参照してください。

**DisplayPhoto** パラメーターの値によって、ユーザーの写真の画像ソースが決定されます。次の表に、サポートされる値を示します。


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>DisplayPhoto パラメーターの値</th>
<th>画像ソース</th>
<th>Lync 2010 クライアントの設定</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NoPhoto</p></td>
<td><p>:</p></td>
<td><p><strong>マイ ピクチャを表示しない</strong></p></td>
</tr>
<tr class="even">
<td><p>PhotoFromADOnly</p></td>
<td><p>Active Directory</p></td>
<td><p><strong>既定のコーポレート ピクチャ</strong></p></td>
</tr>
<tr class="odd">
<td><p>AllPhotos</p></td>
<td><p>Web アドレス</p></td>
<td><p><strong>Web アドレスからピクチャを表示する</strong></p></td>
</tr>
</tbody>
</table>


## Lync 2010 クライアントが写真を取得する方法

Lync 2010 では、ユーザーの写真はアドレス帳サービスによってサーバーで管理されます。Lync クライアントでは、ユーザーの写真を取得するために、最初にサーバーのアドレス帳 Web クエリ (ABWQ) サービスにクエリを実行し、それが配布リスト展開 Web サービス経由で公開されます。クライアントでは画像ファイルを受信してユーザーのキャッシュにコピーするので、表示するたびに画像をダウンロードする必要がなくなります。クエリから返される属性値は、ユーザーのアドレス帳サービス エントリのキャッシュにも保存されます。アドレス帳サービスでは、キャッシュされたすべての画像が24 時間ごとに削除されます。すなわち、サーバーのキャッシュで新しいユーザーの画像に更新されるまでの時間は、最大で 24 時間です。キャッシュを強制的に更新する場合は、[Update-CsAddressBook](update-csaddressbook.md) コマンドレットを使用します。

プレゼンス状態に含まれるユーザーの写真にもハッシュ値が関連付けられ、それを Lync クライアントが使用してさらに新しい画像を使用できるかどうかを判断します。クライアントには、プレゼンス状態で使用される画像ファイルの変更について自動的に通知されます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>写真は GalContacts.db データベースには保存されないため、ユーザー写真のダウンロードはクライアント ポリシーの <strong>AddressBookAvailability</strong> の設定 (<a href="http://go.microsoft.com/fwlink/p/?linkid=507508">Set-CsClientPolicy</a>) には依存しません。</td>
</tr>
</tbody>
</table>


ABWQ サービスに対するクエリの属性には、次のものがあります。

  - **PhotoHash**   写真のバイナリ データのハッシュ値で、現在の写真が変更されているかどうかを判断するために使用されます。

  - **PhotoRelPath**   サーバーに保存されている画像ファイルへの相対パスです。

  - **PhotoSize**   画像ファイルのサイズ (バイト単位) です。

  - **TimeStamp**   画像ファイルが最後にサーバーからダウンロードされてクライアント キャッシュにコピーされた日時です。

次に、画像ファイルの取得後、Lync 2010 クライアントは、クエリから返された属性値とインバンド プロビジョニングから受け取った属性値を比較して、異なるかどうかを確認します。それらの値が異なる場合、クライアントは HTTP GET 要求によってサインインしたユーザーの画像ファイルを取得します。

さらに、クライアントは、画像ファイルのキャッシュされたバージョンが作成された時間から 24 時間ごとにサーバーを確認し、サーバーの **PhotoHash** 属性の値とクライアント上のその値を比較して、それらの値が異なる場合は画像ファイルが変更されていると解釈します。更新された画像ファイルを取得するために、クライアントは再び ABWQ サービスにクエリを実行して、クライアント キャッシュの画像ファイルをサーバーの画像ファイルで更新し、同時にクライアント キャッシュのファイルの **TimeStamp** も更新します。

次に、ABWQ サービスに実行したクエリに対する応答の例を示します。

    <Attribute>
              <Name>PhotoRelPath</Name>
              <Value>efa6096aed2746cb9ab2037f7dbdde9d.f2eeeb5946db54a7aa607ecd3ae09d
              95.photo</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
              <Name>PhotoHash</Name>
              <Value>f2eeeb5946db54a7aa607ecd3ae09d95</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
         <Name>PhotoSize</Name>
         <Value>4620</Value>
         <Valuesxmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays"
    i:nil="true" />
    </Attribute>

## Lync 2013 のユーザーの写真

Lync 2013 では、ユーザーの写真に対する高解像度画像のサポートが導入されています。また、Lync 2013 では、Exchange 2013 のユーザーのメールボックスでもユーザーの写真の保存がサポートされ、Lync 2010 の場合の画像の解像度やサイズの制限がなくなりました。Lync 2013 のユーザーの写真では、最大ピクセル数は 648 × 648、ファイル サイズの上限は 20 MB になります。Lync 2013 の高解像度写真は、Exchange 2013 のユーザーのメールボックスに格納される必要があるため、Lync 2013 クライアントのみでサポートされます。このように Exchange と統合されることで、Lync、Exchange、および SharePoint の 2013 バージョンに含まれる新しい承認フレームワーク (Oauth) を活用できます。

使用している展開で Exchange 2013 が使用されない場合、ユーザーの写真のサポートは Lync 2010 と同じになります。ただし、使用する写真を選ぶためのユーザーの選択肢は、Lync 2013 クライアントでは異なります。Lync 2013 クライアントでは、ユーザーは \[**写真を表示しない**\] または \[**写真を表示する**\] を選べます。\[**Web サイトの写真を表示する**\] は、既定では選べませんが、クライアント ポリシーを割り当てると有効になります。

## 写真を表示しない

ユーザーの写真の設定は、Lync 2013 の \[**オプション**\] ダイアログで実行します。\[**写真を表示しない**\] を選んだ場合、Lync クライアントではユーザーの写真が表示されませんが、自分の連絡先カードや Lync 以外では表示されます。

## 写真を表示する

\[**写真を表示する**\] を選んだ場合、ユーザーの写真は Lync クライアントで表示され、Lync 会話の際には他のユーザーに表示されます。使用される画像は、AD DS に保存されたものです。

## Web サイトの写真を表示する

\[**Web サイトの写真を表示する**\] オプションを Lync 2013 で使用可能にするには、クライアント ポリシーによって有効になるように設定します。クライアントのバージョンは 15.0.4535.1002 以上 ([Lync 2013 15.0.4551.1005 更新プログラムの説明: 2013 年 11 月 7 日](http://go.microsoft.com/fwlink/p/?linkid=509908) でインストールされます) の必要があります。場合によっては、クライアントの変更を確認するために、ユーザーはログアウトしてから再度ログインする必要があります。

クライアント ポリシーを設定して \[**Web サイトの写真を表示する**\] を有効にするには、Lync Server 管理シェル で [Set-CsClientPolicy](set-csclientpolicy.md) ポリシーを実行します。次に、使用している展開のすべてのユーザーに対してグローバルに適用されるポリシーを設定するコマンドレットの例を示します。

    $pe=New-CsClientPolicyEntry -Name EnablePresencePhotoOptions -Value True

   &nbsp;

    $po=Get-CsClientPolicy -Identity Global

   &nbsp;

    $po.PolicyEntry.Add($pe)

   &nbsp;

    Set-CsClientPolicy -Instance $po

画像がユーザーのメールボックスにアップロードされると、Exchange で自動的に画像の低解像度のバージョンが作成され、それをクライアント アプリケーションで使用できます。AD DS でも、ユーザーの写真が更新されます。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412781.note(OCS.15).gif" title="note" alt="note" />注:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>画像ファイルが AD DS で更新されると、48 x 48 ピクセルの画像が作成され、AD DS の thumbnailPhoto に使用されます。既存の画像はすべて置換されます。そのため、AD DS に 96 × 96 の画像を追加すると、新しい 48 × 48 の画像で上書きされます。これは、その環境のユーザーが Lync 2010 クライアント (AD DS からユーザーの写真を取得する) を使用している場合にのみ重要です。組織に Lync 2010 クライアントがいる場合は、96 × 96 ピクセルの画像をインポートして、AD DS で作成された画像を置換できます。</td>
</tr>
</tbody>
</table>


## Lync 2013 のユーザーの写真のサポート

Lync 2013 では、ユーザーの写真に対して 3 つの画像解像度がサポートされます (次の表で示します)。使用される画像は、Lync ユーザーに割り当てられたクライアント ポリシー設定で決定されます。詳細については、このトピックの「クライアント ポリシー コマンドレットによるユーザーの写真の管理」を参照してください。


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>画像解像度 (ピクセル)</th>
<th>Application</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>48 x 48</p></td>
<td><p>高解像度の画像が選択されていないときに使用</p></td>
</tr>
<tr class="even">
<td><p>96 x 96</p></td>
<td><p>Outlook Web App および Outlook 2013 で使用</p></td>
</tr>
<tr class="odd">
<td><p>648 x 648</p></td>
<td><p>Lync 2013 デスクトップ クライアントおよび Lync 2013 Web App で使用</p></td>
</tr>
</tbody>
</table>


Exchange 2013 でメールボックスが有効になっているユーザーは、Outlook Web Access または Lync 2013 クライアント オプション経由で別の画像 (高解像度写真を含む) をアップロードできます。使用する画像に推奨される設定は、次のとおりです。

  - \[**画像の解像度**\]   648 × 648 ピクセル

  - \[**色深度**\]   24 ビット

  - \[**画像ファイルのサイズ**\]   最大 20 MB

  - \[**ファイル形式**\]   JPEG

通常の 24 ビット JPEG 画像は 648 × 648 ピクセルで、ファイル サイズは約 240 KB なので、ユーザーの写真 4 枚ごとに 1 MB の記憶域が必要になります。

