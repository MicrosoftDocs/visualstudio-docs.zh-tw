---
title: 元件索引標籤、工具箱
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a05ea5b06e985a21fbe45882ccfb36bfe194034
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947946"
---
# <a name="toolbox-components-tab"></a>元件索引標籤、工具箱

顯示您可以新增至 Visual Basic 和 C# 設計工具的元件。 除了 Visual Studio隨附的 .NET Framework 元件之外 (例如 <xref:System.Messaging.MessageQueue> 和 <xref:System.Diagnostics.EventLog> 元件)，您還可以將您自己的元件或協力廠商元件新增至這個索引標籤。

 若要顯示這個索引標籤，請從 [檢視] 功能表中選取 [工具箱]。 在 [工具箱] 中，選取 [元件] 索引標籤。

 **BackgroundWorker**

 建立可在個別專用執行緒上執行作業的 `System.ComponentModel.BackgroundWorker` 元件執行個體。

 **DirectoryEntry**

 建立 <xref:System.DirectoryServices.DirectoryEntry> 元件執行個體，以封裝 Active Directory 階層中的節點或物件，而且可以用來與 Active Directory 服務提供者互動。

 **DirectorySearcher**

 建立可用來對 Active Directory 執行查詢的 <xref:System.DirectoryServices.DirectorySearcher> 元件執行個體。

 **ErrorProvider**

 建立 `System.Windows.Forms.ErrorProvider` 元件執行個體，以向使用者指出表單上的控制項具有相關聯的錯誤。

 **EventLog**

 建立可用來與系統和自訂事件記錄檔互動的 <xref:System.Diagnostics.EventLog> 元件執行個體，包括將事件寫入記錄檔以及讀取記錄檔資料。

 **FileSystemWatcher**

 建立 <xref:System.IO.FileSystemWatcher> 元件執行個體，以用來監視您具有存取權之任何目錄或檔案的變更。

 **HelpProvider**

 建立 `System.Windows.Forms.HelpProvider` 元件執行個體，以提供控制項的快顯畫面或線上說明。

 **ImageList**

 建立 `System.Windows.Forms.ImageList` 元件執行個體，以提供方法來管理 `System.Drawing.Image` 物件集合。

 **MessageQueue**

 建立可用來與訊息佇列互動的 <xref:System.Messaging.MessageQueue> 元件執行個體，包括從佇列中讀取訊息與將訊息寫入其中、處理交易，以及執行佇列管理工作。

 **PerformanceCounter**

 建立可用來與 Windows 效能計數器互動的 <xref:System.Diagnostics.PerformanceCounter> 元件執行個體，包括建立新的類別和執行個體、讀取計數器中的值，以及對計數器資料執行計算。

 **Process**

 建立 <xref:System.Diagnostics.Process> 元件執行個體，以用來停止、啟動和操作與系統上的處理序建立關聯的資料。

 **SerialPort**

 建立 `System.IO.Ports.SerialPort` 元件執行個體，以提供同步和事件驅動的 I/O、Pin 和中斷狀態的存取權，以及序列驅動程式屬性的存取權。

 **ServiceController**

 建立可用來操作現有服務的 <xref:System.ServiceProcess.ServiceController> 元件執行個體，包括啟動和停止服務，以及將命令傳送給它們。

 **Timer**

 建立 <xref:System.Windows.Forms.Timer> 元件執行個體，以用來將以時間為基礎的功能新增至 Windows 應用程式。 如需詳細資訊，請參閱 [Timer 元件](/dotnet/framework/winforms/controls/timer-component-windows-forms)。

> [!NOTE]
> 還會有以系統為基礎的 <xref:System.Timers.Timer> 可以新增至 [工具箱]。這個 <xref:System.Timers.Timer> 已針對伺服器應用程式最佳化，而且 Windows Forms <xref:System.Windows.Forms.Timer> 最適合在 Windows Forms 上使用。


## <a name="see-also"></a>另請參閱

- [使用元件進行程式設計](http://msdn.microsoft.com/Library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
- [元件程式設計逐步解說](http://msdn.microsoft.com/Library/373cacf7-479e-4b05-991c-5cb18824e913)
- [工具箱](../../ide/reference/toolbox.md)