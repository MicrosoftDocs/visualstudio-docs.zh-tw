---
title: 從 伺服器總管存取 Azure 虛擬機器 |Microsoft Docs
description: 本文概述如何檢視建立和管理 Azure 虛擬機器 (Vm) 在 Visual Studio 中的 [伺服器總管] 中。
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: e1410b3dc60ec9689b6582e794aaf10cd13092aa
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001398"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>從伺服器總管存取 Azure 虛擬機器

如果您有 Azure 主控的虛擬機器時，您可以在 [伺服器總管] 中存取它們。 您必須先登入您的 Azure 訂用帳戶若要檢視您的行動服務。 若要登入，請在 [伺服器總管] 中，開啟 Azure 節點的捷徑功能表，然後選擇**連接到 Microsoft Azure**。

1. 在 [雲端總管] 中，選擇虛擬機器，然後選擇 F4 鍵以顯示其屬性視窗。

    下表顯示哪些屬性可供使用，但所有唯讀模式。 若要加以變更，請使用[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)。

   | 屬性 | 描述 |
   | --- | --- |
   | DNS 名稱 |包含虛擬機器的網際網路位址的 URL。 |
   | 環境 |對於虛擬機器時，這個屬性的值一律是生產環境。 |
   | 名稱 |虛擬機器的名稱。 |
   | 大小 |虛擬機器，這會反映記憶體和磁碟可用空間量的大小。 如需詳細資訊，請參閱 <<c0> [ 虛擬機器大小](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs)。 |
   | 狀態 |值包括啟動、 已啟動、 停止、 已停止 」 和擷取的狀態。 如果出現 正在擷取狀態，目前的狀態是未知的。 這個屬性的值不同於所使用的值[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)。 |
   | SubscriptionID |您的 Azure 帳戶的訂用帳戶識別碼。 您可以將這項資訊顯示在[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)透過檢視訂用帳戶的屬性。 |
2. 選擇端點節點，然後再檢視**屬性**視窗。
3. 下表描述可用的端點屬性，但它們是唯寫。 若要新增或編輯虛擬機器的端點，請使用[Azure 入口網站](http://go.microsoft.com/fwlink/p/?LinkID=525040)。 

   | 屬性 | 描述 |
   | --- | --- |
   | 名稱 |端點的識別碼。 |
   | 私人連接埠 |您的應用程式的內部網路存取連接埠。 |
   | 通訊協定 |使用的通訊協定為此端點的傳輸層，TCP 或 UDP。 |
   | 公用連接埠 |使用於您的應用程式的公用存取連接埠。 |
