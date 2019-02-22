---
title: 如何：收集 Windows 事件追蹤 (ETW) 資料 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 74754feccc37e32164fe03b156cf059695e7fe66
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793057"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>如何：收集 Windows 事件追蹤 (ETW) 資料
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows 事件追蹤 (ETW) 是高效率的核心層級追蹤功能，可讓程式碼剖析工具記錄核心或應用程式定義的事件。 從事件提供者收集的資料，只能透過 /**Summary:ETW** option of the [VSPerfReport](../profiling/vsperfreport.md)命令列工具檢視。 您可使用此報告來判斷應用程式中發生效能問題的癥結。  
  
 **需求**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Windows 8 和 Windows Server 2012 增強式安全性功能需要的重大變更，會以 Visual Studio 分析工具在這些平台收集資料的方式表現。 Windows 市集應用程式也需要新的資料收集技術。 請參閱 [Windows 8 和 Windows Server 2012 應用程式的效能工具](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)。  
  
### <a name="to-enable-event-trace-providers"></a>啟用事件追蹤提供者  
  
1.  在 [效能總管] 中，以滑鼠右鍵按一下效能工作階段，然後按一下 [屬性] 。  
  
2.  在 [屬性頁] 中，按一下 [Windows 事件]  屬性。  
  
3.  在 [選取要從中收集資料的事件追蹤提供者] 清單中，選取要用來對應用程式進行程式碼剖析的事件提供者。  
  
## <a name="see-also"></a>請參閱  
 [設定效能工作階段](../profiling/configuring-performance-sessions.md)
