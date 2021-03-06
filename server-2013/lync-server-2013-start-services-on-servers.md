﻿---
title: 'Lync Server 2013: サーバーでのサービスの開始'
TOCTitle: サーバーでのサービスの開始
ms:assetid: fa26eaed-0529-4f32-9f3f-f32c4bd4b1c8
ms:mtpsurl: https://technet.microsoft.com/ja-jp/library/Gg413059(v=OCS.15)
ms:contentKeyID: 48274115
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 のサーバーでのサービスの開始

 

_**トピックの最終更新日:** 2014-09-03_

この手順を正常に完了するには、RTCUniversalServerAdmins グループのメンバーとしてログオンしているか、適切なアクセス許可が委任されている必要があります。アクセス許可委任の詳細については、「[Lync Server 2013 でのセットアップのアクセス許可の委任](lync-server-2013-delegate-setup-permissions.md)」を参照してください。

サーバーへのローカル構成ストアのインストール、 Lync Server 2013 コンポーネントのインストール、および フロント エンド サーバーまたは フロント エンド サーバーの証明書構成を完了したら、このサーバーで Lync Server 2013 サービスを開始する必要があります。以下の手順に従い、展開で フロント エンド サーバーごとにサービスを開始してください。

## Standard Edition またはフロントエンド サーバーでサービスを開始するには

1.  Lync Server 展開ウィザードで、 **Lync Server 2013** ページの \[**ステップ 4: サービスの開始**\] の横にある \[**実行**\] をクリックします。

2.  \[**サービスの開始**\] ページで \[**次へ**\] をクリックして、サーバー上で Lync Server サービスを開始します。

3.  すべてのサービスが正常に開始されたら、\[**コマンドの実行**\] ページで \[**終了**\] をクリックします。
    

    > [!IMPORTANT]
    > サーバーのサービスを開始するコマンドは、サービスが事実上開始されたことをレポートするベストエフォート型の方法です。サービスの実際の状態を反映していない場合もあります。[<STRONG>サービスの開始</STRONG>] の直後に、ステップ [<STRONG>サービスの状態 (オプション)</STRONG>] で Microsoft 管理コンソール (MMC) を開き、サービスが正常に開始されたことを確認することをお勧めします。 Lync Server のいずれかのサービスが開始していない場合は、MMC でそのサービスを右クリックし、[<STRONG>開始</STRONG>] をクリックします。


