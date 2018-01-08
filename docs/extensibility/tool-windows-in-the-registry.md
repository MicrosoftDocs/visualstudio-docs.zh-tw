---
title: "工具視窗在登錄中的 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8d3277a4e24b12d409654548b5670a4d47fa9539
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="tool-windows-in-the-registry"></a>在登錄中的工具視窗
提供的工具視窗的 Vspackage 必須向[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]做為工具視窗提供者。 使用 Visual Studio 封裝範本所建立的工具視窗這麼做的預設值。 工具視窗提供者具有指定可視性的屬性，例如預設工具視窗大小和位置，做為工具視窗窗格和停駐樣式的視窗 GUID 的系統登錄機碼。  
  
 在開發期間，受管理的工具視窗提供者會將屬性加入至原始程式碼中，並在產生的組件上執行 RegPkg.exe 公用程式註冊工具視窗。 如需詳細資訊，請參閱[註冊工具視窗](../extensibility/registering-a-tool-window.md)。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>註冊未受管理的工具視窗提供者  
 未受管理的工具視窗提供者必須向[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]系統登錄的 ToolWindows 區段中。 下列.reg 檔案片段顯示動態工具視窗可能會註冊方式：  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 在上述範例中的第一個索引鍵，版本號碼是版本[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，例如 7.1 或 8.0、 子機碼 {f0e1e9a1-9860-484d-ad5d-367d79aabf55} 是工具視窗窗格 (DynamicWindowPane)，以及預設值 {的 GUID01069cdd-95ce-4620-ac21-ddff6c57f012} 是 VSPackage 提供的工具視窗的 GUID。 如需 Float 和 DontForceCreate 子機碼的說明，請參閱[工具視窗顯示組態](../extensibility/tool-window-display-configuration.md)。  
  
 第二個選擇性金鑰 ToolWindows\Visibility，指定之 Guid 的要求將會看見 [工具] 視窗的命令。 在此情況下，沒有指定任何命令。 如需詳細資訊，請參閱[工具視窗顯示組態](../extensibility/tool-window-display-configuration.md)。  
  
## <a name="see-also"></a>請參閱  
 [VSPackage](../extensibility/internals/vspackages.md)