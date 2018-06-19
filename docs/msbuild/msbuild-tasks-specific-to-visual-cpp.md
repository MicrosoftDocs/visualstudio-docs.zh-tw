---
title: Visual C++ 特有的 MSBuild 工作 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 446326fb8219183774d3f90d70a0263e0fc057e0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/19/2018
ms.locfileid: "31573755"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Visual C++ 特有的 MSBuild 工作
提供在建置流程期間執行之程式碼的工作。 安裝 Visual C++ 之後，除了已隨 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 安裝的工作之外，還會有下列工作可供使用。 如需詳細資訊，請參閱 [MSBuild (Visual C++) 概觀](/cpp/build/msbuild-visual-cpp-overview)。  
  
 除了適用於每個工作的參數之外，每個工作也會有下列參數。  
  
|參數|描述|  
|---------------|-----------------|  
|`Condition`|選擇性的 `String` 參數。<br /><br /> `Boolean` 運算式，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 引擎會使用此運算式來決定是否要執行此工作。 如需 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 所支援條件的相關資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。|  
|`ContinueOnError`|選擇性參數。 可包含一或多個下列值：<br /><br /> -   **WarnAndContinue** 或 **true**。 當工作失敗時，[Target](../msbuild/target-element-msbuild.md) 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為警告。<br />-   **ErrorAndContinue**。 當工作失敗時，`Target` 項目中的後續工作與組建都會繼續執行，並將來自工作的所有錯誤視為錯誤。<br />-   **ErrorAndStop** 或 **false** (預設值)。 當工作失敗時，就不會執行 `Target` 項目中的其餘工作和組建，並將整個 `Target` 項目與組建視為失敗。<br /><br /> 只有 4.5 版之前的 .NET Framework 版本支援 `true` 和 `false` 值。<br /><br /> 如需詳細資訊，請參閱[如何：忽略工作中的錯誤](../msbuild/how-to-ignore-errors-in-tasks.md)。|  
  
## <a name="related-topics"></a>相關主題  
  
|標題|描述|  
|-----------|-----------------|  
|[BscMake 工作](../msbuild/bscmake-task.md)|包裝 Microsoft Browse Information Maintenance Utility 工具 (bscmake.exe)。|  
|[CL 工作](../msbuild/cl-task.md)|包裝 Visual C++ 編譯器工具 (cl.exe)。|  
|[CPPClean 工作](../msbuild/cppclean-task.md)|刪除在建置 Visual C++ 專案時由 MSBuild 所建立的暫存檔。|  
|[LIB 工作](../msbuild/lib-task.md)|包裝 Microsoft 32 位元程式庫管理員工具 (lib.exe)。|  
|[Link 工作](../msbuild/link-task.md)|包裝 Visual C++ 連結器工具 (link.exe)。|  
|[MIDL 工作](../msbuild/midl-task.md)|包裝 Microsoft 介面定義語言 (MIDL) 編譯器工具 (midl.exe)。|  
|[MT 工作](../msbuild/mt-task.md)|包裝 Microsoft 資訊清單工具 (mt.exe)。|  
|[RC 工作](../msbuild/rc-task.md)|包裝 Microsoft Windows 資源編譯器工具 (rc.exe)。|  
|[SetEnv 工作](../msbuild/setenv-task.md)|設定或刪除指定環境變數的值。|  
|[VCMessage 工作](../msbuild/vcmessage-task.md)|在建置期間記錄警告訊息和錯誤訊息。|  
|[XDCMake 工作](../msbuild/xdcmake-task.md)|包裝 XML 文件工具 (xdcmake.exe)，此工具可將 XML 文件註解 (.xdc) 檔案合併至 .xml 檔案。|  
|[XSD 工作](../msbuild/xsd-task.md)|包裝 XML 結構描述定義工具 (xsd.exe)，其會從來源產生結構描述或類別檔案。|  
|[MSBuild 參考](../msbuild/msbuild-reference.md)|描述 MSBuild 系統的項目。|  
|[工作](../msbuild/msbuild-tasks.md)|描述工作，也就是可結合以產生組建的程式碼單位。|  
|[工作撰寫](../msbuild/task-writing.md)|描述如何建立工作。|