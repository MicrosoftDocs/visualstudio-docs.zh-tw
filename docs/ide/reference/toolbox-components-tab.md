---
title: 元件索引標籤、工具箱
description: 瞭解您可以在 [工具箱] 視窗的 [元件] 索引標籤中找到的元件。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: adbc2611cf0d0e08ef356e91e25ed0c4854c4386
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965040"
---
# <a name="toolbox-components-tab"></a>工具箱, 元件索引標籤

顯示您可以新增至 Windows Forms 之 Visual Basic 和 C# 設計工具的元件。 除了 Visual Studio 隨附的 .NET 元件 (例如 <xref:System.Messaging.MessageQueue> 和 <xref:System.Diagnostics.EventLog> 元件) 之外，您還可以將您自己的元件或協力廠商元件新增至這個索引標籤。

若要顯示此索引標籤，請開啟 Windows Forms 設計工具。 選取 [ **View**  >  **工具箱**]。 在 [工具箱] 中，選取 [元件] 索引標籤。

## <a name="components"></a>單元

**BackgroundWorker**

建立可在個別專用執行緒上執行作業的 <xref:System.ComponentModel.BackgroundWorker> 元件執行個體。 如需詳細資訊，請參閱 [BackgroundWorker 元件](/dotnet/framework/winforms/controls/backgroundworker-component)。

**DirectoryEntry**

建立 <xref:System.DirectoryServices.DirectoryEntry> 元件執行個體，以封裝 Active Directory 階層中的節點或物件，而且可以用來與 Active Directory 服務提供者互動。

**DirectorySearcher**

建立可用來對 Active Directory 執行查詢的 <xref:System.DirectoryServices.DirectorySearcher> 元件執行個體。

**ErrorProvider**

建立 <xref:System.Windows.Forms.ErrorProvider> 元件執行個體，以向使用者指出表單上的控制項具有相關聯的錯誤。 如需詳細資訊，請參閱 [ErrorProvider 元件](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms)。

**EventLog**

建立可用來與系統和自訂事件記錄檔互動的 <xref:System.Diagnostics.EventLog> 元件執行個體，包括將事件寫入記錄檔以及讀取記錄檔資料。

**FileSystemWatcher**

建立 <xref:System.IO.FileSystemWatcher> 元件執行個體，以用來監視您具有存取權之任何目錄或檔案的變更。

**HelpProvider**

建立 <xref:System.Windows.Forms.HelpProvider> 元件執行個體，以提供控制項的快顯畫面或線上說明。 如需詳細資訊，請參閱 [HelpProvider 元件](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms)。

**ImageList**

建立 <xref:System.Windows.Forms.ImageList> 元件執行個體，以提供方法來管理 <xref:System.Drawing.Image> 物件集合。 如需詳細資訊，請參閱 [ImageList 元件](/dotnet/framework/winforms/controls/imagelist-component-windows-forms)。

**MessageQueue**

建立可用來與訊息佇列互動的 <xref:System.Messaging.MessageQueue> 元件執行個體，包括從佇列中讀取訊息與將訊息寫入其中、處理交易，以及執行佇列管理工作。

**PerformanceCounter**

建立可用來與 Windows 效能計數器互動的 <xref:System.Diagnostics.PerformanceCounter> 元件執行個體，包括建立新的類別和執行個體、讀取計數器中的值，以及對計數器資料執行計算。

**處理**

建立 <xref:System.Diagnostics.Process> 元件執行個體，以用來停止、啟動和操作與系統上的處理序建立關聯的資料。

**SerialPort**

建立 <xref:System.IO.Ports.SerialPort> 元件執行個體，以提供同步和事件驅動的 I/O、Pin 和中斷狀態的存取權，以及序列驅動程式屬性的存取權。

**ServiceController**

建立可用來操作現有服務的 <xref:System.ServiceProcess.ServiceController> 元件執行個體，包括啟動和停止服務，以及將命令傳送給它們。

**計時器**

建立 <xref:System.Windows.Forms.Timer> 元件執行個體，以用來將以時間為基礎的功能新增至 Windows 應用程式。 如需詳細資訊，請參閱 [計時器元件](/dotnet/framework/winforms/controls/timer-component-windows-forms)。

> [!NOTE]
> 還會有以系統為基礎的 <xref:System.Timers.Timer> 可以新增至 [工具箱]。這個 <xref:System.Timers.Timer> 已針對伺服器應用程式最佳化，而且 Windows Forms <xref:System.Windows.Forms.Timer> 最適合在 Windows Forms 上使用。

## <a name="see-also"></a>另請參閱

- [要在 Windows Forms 上使用的控制項](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [選擇工具箱項目、WPF 元件](choose-toolbox-items-wpf-components.md)
- [工具箱](../../ide/reference/toolbox.md)
