---
title: インクルード ファイル
description: インクルード ファイル
services: vpn-gateway
author: cherylmc
ms.service: vpn-gateway
ms.topic: include
ms.date: 09/28/2019
ms.author: cherylmc
ms.custom: include file
ms.openlocfilehash: cf9d4c3fd96df83361e7d9aa89ba702d37265ec6
ms.sourcegitcommit: c95e2d89a5a3cf5e2983ffcc206f056a7992df7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95556717"
---
0\.0.0.0/0 が宛先のユーザー定義のルートと GatewaySubnet の NSG は **サポートされていません**。 この構成で作成されたゲートウェイの作成はブロックされます。 ゲートウェイが正常に機能するためには、管理コントローラーへのアクセスが必要です。 ゲートウェイの可用性を確保するために、GatewaySubnet で [[BGP ルート伝達]](../articles/virtual-network/virtual-networks-udr-overview.md#border-gateway-protocol) を [有効] に設定する必要があります。 これが無効に設定されていると、ゲートウェイは機能しません。