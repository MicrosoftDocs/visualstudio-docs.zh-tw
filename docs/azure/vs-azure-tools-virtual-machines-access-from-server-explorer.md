---
title: 從伺服器總管存取 Azure 虛擬機器 | Microsoft Docs
description: 取得如何在 Visual Studio 的 [伺服器總管] 中，檢視建立和管理 Azure 虛擬機器 (VM) 的概觀。
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: a40434845187490ee4f8437f8e15963bddd1998f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99843783"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>從伺服器總管存取 Azure 虛擬機器

如果您有 Azure 主控的虛擬機器，您可以在 [伺服器總管] 中存取它們。 您必須先登入您的 Azure 訂用帳戶，才能檢視您的行動服務。 若要登入，請在 [伺服器總管] 中開啟 [Azure] 節點的捷徑功能表，並選擇 [連線到 Microsoft Azure] 。

1. 在 Cloud Explorer 中選擇虛擬機器，然後選擇 F4 鍵以顯示其屬性視窗。

    下表顯示可以使用的屬性，但他們全部都是唯讀。 若要加以變更，請使用 [Azure 入口網站](https://portal.azure.com)。

   | 屬性 | 描述 |
   | --- | --- |
   | DNS 名稱 |包含虛擬機器網際網路位址的 URL。 |
   | 環境 |若是虛擬機器，這個屬性的值一定是 [生產]。 |
   | 名稱 |虛擬機器的名稱。 |
   | 大小 |虛擬機器的大小，此值會反映可用的記憶體和磁碟空間數量。 如需詳細資訊，請參閱 [虛擬機器大小](/azure/cloud-services/cloud-services-sizes-specs)。 |
   | 狀態 |值包括 [啟動中]、[已啟動]、[停止中]、[已停止] 和 [正在擷取狀態]。 如果出現 [正在擷取狀態]，則目前狀態是未知的。 這個屬性的值不同於 [Azure 入口網站](https://portal.azure.com)上所使用的值。 |
   | SubscriptionID |Azure 帳戶的訂用帳戶識別碼。 您可以透過檢視訂用帳戶的屬性，在 [Azure 入口網站](https://portal.azure.com)上顯示這項資訊。 |
2. 選擇端點節點，然後檢視 [**屬性**] 視窗。
3. 下表說明可用的端點屬性，但他們全部都是唯讀。 若要新增或編輯虛擬機器的端點，請使用 [Azure 入口網站](https://portal.azure.com)。

   | 屬性 | 描述 |
   | --- | --- |
   | 名稱 |端點的識別碼 |
   | 私人連接埠 |網路內部存取應用程式的連接埠。 |
   | 通訊協定 |此端點的傳輸層所使用的通訊協定：TCP 或 UDP。 |
   | 公用連接埠 |提供公用存取應用程式使用的通訊埠。 |
