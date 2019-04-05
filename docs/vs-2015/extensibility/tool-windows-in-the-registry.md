---
title: 工具在登錄中的 Windows |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58941459"
---
# <a name="tool-windows-in-the-registry"></a>在登錄中的工具 Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

提供的工具視窗的 Vspackage 必須向[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]做為工具視窗提供者。 使用 Visual Studio Package 範本所建立的工具視窗會依預設此進行。 工具視窗提供者都有系統的登錄機碼指定可見性屬性，例如工具視窗的預設大小和位置，做為工具視窗窗格中，並停駐樣式的視窗的 GUID。  
  
 在開發期間，受管理的工具視窗提供者會透過將屬性加入至原始程式碼，並在產生的組件上執行 RegPkg.exe 公用程式註冊工具視窗。 如需詳細資訊，請參閱 <<c0> [ 註冊的工具視窗](../extensibility/registering-a-tool-window.md)。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>註冊不受管理的工具視窗提供者  
 未受管理的工具視窗提供者必須向[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ToolWindows 部分系統登錄中。 下列.reg 檔案片段顯示動態工具視窗可能會註冊方式：  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 在上述範例中的第一個索引鍵，版本號碼是版本[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]，例如 7.1 或 8.0，子機碼 {f0e1e9a1-9860-484d-ad5d-367d79aabf55} 是工具視窗窗格 (DynamicWindowPane)，以及預設值 {的 GUID01069cdd-95ce-4620-ac21-ddff6c57f012} 是 VSPackage 提供 [工具] 視窗的 GUID。 如需浮點和 DontForceCreate 子機碼的說明，請參閱 <<c0> [ 工具視窗中顯示組態](../extensibility/tool-window-display-configuration.md)。  
  
 第二個選擇性金鑰，而 ToolWindows\Visibility，指定要求將會看見 [工具] 視窗的命令的 Guid。 在此情況下，沒有指定的命令。 如需詳細資訊，請參閱 <<c0> [ 工具視窗中顯示組態](../extensibility/tool-window-display-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage 基本資訊](../misc/vspackage-essentials.md)
