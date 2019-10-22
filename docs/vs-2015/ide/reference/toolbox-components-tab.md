---
title: 元件索引標籤、工具箱 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661573"
---
# <a name="toolbox-components-tab"></a>元件索引標籤、工具箱
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

顯示您可以新增至 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 和 [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 設計工具的元件。 除了 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 隨附的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 元件之外 (例如 <xref:System.Messaging.MessageQueue> 和 <xref:System.Diagnostics.EventLog> 元件)，您還可以將您自己的元件或協力廠商元件新增至這個索引標籤。如需詳細資訊，請參閱[如何：操作工具箱索引標籤](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db)。

 若要顯示這個索引標籤，請從 [檢視]  功能表中選取 [工具箱]  。 在 [工具箱]  中，選取 [元件]  索引標籤。

 **BackgroundWorker**建立可在個別的專用線程上執行作業的 `System.ComponentModel.BackgroundWorker` 元件實例。

 **DirectoryEntry**建立 <xref:System.DirectoryServices.DirectoryEntry> 元件實例，以封裝 Active Directory 階層中的節點或物件，並可用來與 Active Directory 服務提供者互動。

 **DirectorySearcher**建立 <xref:System.DirectoryServices.DirectorySearcher> 元件實例，您可以用來對 Active Directory 執行查詢。

 **ErrorProvider**建立 `System.Windows.Forms.ErrorProvider` 元件實例，這會向使用者指出表單上的控制項有相關聯的錯誤。

 **EventLog**建立可用來與系統和自訂事件記錄檔互動的 <xref:System.Diagnostics.EventLog> 元件實例，包括將事件寫入記錄檔和讀取記錄資料。 如需詳細資訊，請參閱 [EventLog 元件的簡介](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805)。

 **FileSystemWatcher**建立 <xref:System.IO.FileSystemWatcher> 元件實例，您可以用來監視您有權存取之任何目錄或檔案的變更。 如需詳細資訊，請參閱[如何：設定 FileSystemWatcher 元件執行個體](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50)。

 **HelpProvider**建立 `System.Windows.Forms.HelpProvider` 元件實例，以提供控制項的快顯或線上說明。

 **ImageList**建立 `System.Windows.Forms.ImageList` 元件實例，以提供管理 `System.Drawing.Image` 物件集合的方法。

 **MessageQueue**建立可用來與訊息佇列互動的 <xref:System.Messaging.MessageQueue> 元件實例，包括從佇列讀取訊息、將訊息寫入佇列、處理交易，以及執行佇列管理工作。 如需詳細資訊，請參閱[使用訊息元件](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7)。

 **PerformanceCounter**建立可用來與 Windows 效能計數器互動的 <xref:System.Diagnostics.PerformanceCounter> 元件實例，包括建立新的類別和實例、讀取計數器中的值，以及對計數器資料執行計算。 如需詳細資訊，請參閱[監視效能臨界值](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91)。

 **進程**建立 <xref:System.Diagnostics.Process> 元件實例，您可以用來停止、啟動及操作與系統上的處理常式相關聯的資料。 如需詳細資訊，請參閱[監視和管理 Windows 處理序](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e)。

 **SerialPort**建立 `System.IO.Ports.SerialPort` 元件實例，以提供同步和事件驅動的 i/o、pin 和中斷狀態的存取權，以及序列驅動程式屬性的存取權。

 **ServiceController**建立可用來操作現有服務的 <xref:System.ServiceProcess.ServiceController> 元件實例，包括啟動和停止服務，以及將命令傳送給它們。 如需詳細資訊，請參閱[監視 Windows 服務](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222)。

 **計時器**建立 <xref:System.Windows.Forms.Timer> 元件實例，您可以用來將以時間為基礎的功能新增至您的 Windows 應用程式。 如需詳細資訊，請參閱 [Timer 元件](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7)。

> [!NOTE]
> 還會有以系統為基礎的 <xref:System.Timers.Timer> 可以新增至 [工具箱]  。這個 <xref:System.Timers.Timer> 已針對伺服器應用程式最佳化，而且 Windows Forms <xref:System.Windows.Forms.Timer> 最適合在 Windows Forms 上使用。

## <a name="see-also"></a>另請參閱
 [使用元件進行程式設計](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913)逐步解說[工具箱](../../ide/reference/toolbox.md)[選擇工具箱專案對話方塊（Visual Studio）](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
