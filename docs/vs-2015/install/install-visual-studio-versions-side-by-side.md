---
title: 安裝 Visual Studio 版本的並存 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: ae67e83b2f1444c09129ed5242afac2c3939c954
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47498927"
---
# <a name="install-visual-studio-versions-side-by-side"></a>安裝 Visual Studio 版本的並存
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可將此版本的 Visual Studio 安裝在已安裝舊版的電腦上。 如果您遇到安裝失敗的情況，您可以使用 [記錄收集工具](http://go.microsoft.com/fwlink/?LinkId=262077) 收集失敗的資訊，讓您可以偵錯問題。  
  
> [!NOTE]
>  我們建議您安裝[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]版本已發行的順序。 例如，請先安裝 Visual Studio 2013，再安裝 Visual Studio 2015。  
  
 並存安裝多個版本之前，請先檢閱下列狀況：  
  
-   如果您使用 Visual Studio 2015 開啟的方案中建立[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]，您稍後可以開啟並修改方案一次在舊版中的，只要未實作 Visual Studio 2015 特定的任何功能。  
  
-   如果您嘗試使用 Visual Studio 2015 開啟的方案中建立[!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]或較早的版本中，您可能需要修改專案和檔案，才能使用 Visual Studio 2015 相容。 如需詳細資訊，請參閱 <<c0> [ 移植、 移轉及升級 Visual Studio 專案](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md)頁面。  
  
-   如果在已經安裝多個 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的電腦上解除安裝其中一個版本，則會移除所有版本的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 檔案關聯。 您可以藉由重新對應這些檔案關聯**還原檔案關聯**按鈕**環境**，**一般**頁面[選項](../ide/reference/general-environment-options-dialog-box.md)  對話方塊。  
  
-   Visual Studio 不會自動升級擴充功能，因為並非所有擴充功能都相容。 您必須從 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkId=178891) 或軟體發行者重新安裝擴充功能。  
  
## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework 的版本和並存安裝  
  
-   Visual Basic、Visual C# 或 Visual F# 專案中 [專案設計工具]  使用 [目標 Framework]  選項，指定專案的目標 .NET Framework 版本。 對於 C++ 專案，您可以手動修改 .vcxproj 檔案來變更目標 Framework。 如需詳細資訊，請參閱 <<c0> [ 版本相容性](http://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f)。  
  
     當您建立專案時，您可以在 [新增專案]  對話方塊的 [.NET Framework]  清單中指定專案的目標 .NET Framework 版本。  
  
     如需語言特定的資訊，請參閱下表中適當的主題。  
  
    |語言|主題|  
    |--------------|-----------|  
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[專案設計工具、應用程式頁面 (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C#|[專案設計工具，應用程式頁面 (C#)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F#|[設定專案](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|  
    |C++|[如何：修改目標 Framework 和平台工具組](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|  
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[在舊版的 Common Language Runtime 上執行 JScript 應用程式](http://msdn.microsoft.com/en-us/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## <a name="see-also"></a>另請參閱  
 [安裝 Visual Studio](../install/install-visual-studio-2015.md) [移植、 移轉及升級 Visual Studio 專案](../misc/port-migrate-and-upgrade-visual-studio-projects-in-visual-studio-15-rc.md)   
 [建置 C/c + + 隔離應用程式和並排顯示組件](http://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)   
 [Visual Studio 中的自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)