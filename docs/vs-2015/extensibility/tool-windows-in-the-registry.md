---
title: 登錄中的工具視窗 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186376"
---
# <a name="tool-windows-in-the-registry"></a>登錄中的工具視窗
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

提供工具視窗的 Vspackage 必須將註冊 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 為工具視窗提供者。 使用 Visual Studio 套件範本建立的工具視窗預設會進行這項操作。 工具視窗提供者具有系統登錄鍵，可指定可見度屬性，例如預設工具視窗大小和位置、做為工具視窗窗格的視窗 GUID，以及停駐樣式。  
  
 在開發期間，受管理的工具視窗提供者會將屬性新增至原始程式碼，然後在產生的元件上執行 RegPkg.exe 公用程式，以註冊工具視窗。 如需詳細資訊，請參閱 [註冊工具視窗](../extensibility/registering-a-tool-window.md)。  
  
## <a name="registering-unmanaged-tool-window-providers"></a>註冊未受管理的工具視窗提供者  
 未受管理的工具視窗提供者必須 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 在系統登錄的 ToolWindows 區段中註冊。 下列 .reg 檔案片段會顯示動態工具視窗的註冊方式：  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 在上述範例的第一個索引鍵中，版本號碼是的版本（ [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 例如7.1 或8.0），子機碼 {f0e1e9a1-9860-484d-ad5d-367d79aabf55} 是工具視窗窗格的 guid (DynamicWindowPane) ，而預設值為 {01069cdd-95ce-4620-ac21-ddff6c57f012} 是提供工具視窗之 VSPackage 的 guid。 如需 Float 和 DontForceCreate 子機碼的說明，請參閱 [工具視窗顯示設定](../extensibility/tool-window-display-configuration.md)。  
  
 第二個選擇性的索引鍵 ToolWindows\Visibility，指定需要讓工具視窗顯示的命令 Guid。 在此情況下，未指定任何命令。 如需詳細資訊，請參閱 [工具視窗顯示設定](../extensibility/tool-window-display-configuration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [VSPackage 基本資訊](../misc/vspackage-essentials.md)
