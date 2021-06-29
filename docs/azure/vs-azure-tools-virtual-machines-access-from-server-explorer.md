---
title: 從伺服器總管存取 Azure 虛擬機器 | Microsoft Docs
description: 取得如何在 Visual Studio 的 [伺服器總管] 中，檢視建立和管理 Azure 虛擬機器 (VM) 的概觀。
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: f95542c79e6f8cde83866caa082b8e025b069589
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038573"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>從伺服器總管存取 Azure 虛擬機器

::: moniker range=">=vs-2022"
> [!Important]
> 伺服器總管的 Azure 節點已在 Visual Studio 2022 中淘汰。 您可以使用 Azure 入口網站，或繼續使用舊版 Visual Studio 中伺服器總管的 Azure 節點。
>
> 此外， [Microsoft Azure 儲存體總管](/azure/vs-azure-tools-storage-manage-with-storage-explorer) 是 Microsoft 提供的免費獨立應用程式。 您可以使用它在 Windows、macOS 和 Linux 上以視覺化方式處理 Azure 儲存體資料。
>
> 如需 Visual Studio 2022 的詳細資訊，請參閱我們的 [版本](/visualstudio/releases/2022/release-notes-preview/)資訊。

::: moniker-end

::: moniker range="<=vs-2019"

如果您有 Azure 主控的虛擬機器，您可以在 [伺服器總管] 中存取它們。 您必須先登入您的 Azure 訂用帳戶，才能檢視您的行動服務。 若要登入，請在 [伺服器總管] 中開啟 [Azure] 節點的捷徑功能表，並選擇 [連線到 Microsoft Azure] 。

1. 在 Cloud Explorer 中選擇虛擬機器，然後選擇 F4 鍵以顯示其屬性視窗。

    下表顯示可以使用的屬性，但他們全部都是唯讀。 若要加以變更，請使用 [Azure 入口網站](https://portal.azure.com)。

   | 屬性 | 描述 |
   | --- | --- |
   | DNS 名稱 |包含虛擬機器網際網路位址的 URL。 |
   | 環境 |若是虛擬機器，這個屬性的值一定是 [生產]。 |
   | Name |虛擬機器的名稱。 |
   | 大小 |虛擬機器的大小，此值會反映可用的記憶體和磁碟空間數量。 如需詳細資訊，請參閱 [虛擬機器大小](/azure/cloud-services/cloud-services-sizes-specs)。 |
   | 狀態 |值包括 [啟動中]、[已啟動]、[停止中]、[已停止] 和 [正在擷取狀態]。 如果出現 [正在擷取狀態]，則目前狀態是未知的。 這個屬性的值不同於 [Azure 入口網站](https://portal.azure.com)上所使用的值。 |
   | SubscriptionID |Azure 帳戶的訂用帳戶識別碼。 您可以透過檢視訂用帳戶的屬性，在 [Azure 入口網站](https://portal.azure.com)上顯示這項資訊。 |
2. 選擇端點節點，然後檢視 [**屬性**] 視窗。
3. 下表說明可用的端點屬性，但他們全部都是唯讀。 若要新增或編輯虛擬機器的端點，請使用 [Azure 入口網站](https://portal.azure.com)。

   | 屬性 | 描述 |
   | --- | --- |
   | Name |端點的識別碼 |
   | 私人連接埠 |網路內部存取應用程式的連接埠。 |
   | 通訊協定 |此端點的傳輸層所使用的通訊協定：TCP 或 UDP。 |
   | 公用連接埠 |提供公用存取應用程式使用的通訊埠。 |

::: moniker-end