---
title: 如何：設定 Debug 和 Release 設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703649"
---
# <a name="how-to-set-debug-and-release-configurations"></a>如何：設定偵錯和發行組態
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 專案針對您的程式具有不同的版本和偵錯組態。 依照名稱提示，您可以建置用來偵錯的偵錯版本，和最後發行散發的發行版本。  
  
 程式的偵錯組態會使用完整符號偵錯資訊，在沒有最佳化的情況下進行編譯。 最佳化會使偵錯變得複雜，因為原始程式碼與產生的指令之間關係較為複雜。  
  
 程式的發行組態不包含符號偵錯資訊，而且會完全最佳化。 依照所用的編譯器選項而定，PDB 檔案中可能會產生偵錯資訊。 如果您日後必須偵錯發行版本，建立 PDB 檔可能會非常有用。  
  
 如需組建設定的詳細資訊，請參閱 [瞭解組建](../ide/understanding-build-configurations.md)設定。  
  
 您可以從 [ **組建** ] 功能表、工具列，或在專案的屬性頁中變更組建設定。 專案屬性頁因語言而異。 下列程序示範如何從功能表和工具列變更組建組態。 如需如何變更不同語言專案中組建組態的詳細資訊，請參閱以下的＜相關主題＞一節。  
  
### <a name="to-change-the-build-configuration"></a>若要變更組建組態  
  
1. 從 [組建] 功能表中，按一下 [ **建立]/[Configuration Manager**，然後選取 [ **Debug** ] 或 [ **發行**]。  
  
2. 在工具列上，從 [**方案**設定] 清單方塊中選擇 [ **Debug** ] 或 [**發行**]。  
  
     ![工具列組建組態](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     在 Express 版中無法使用此工具列。 您可以使用 **組建方案 F6** 並 **開始調試 F5** 功能表項目，以選擇設定。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯工具設定和準備](../debugger/debugger-settings-and-preparation.md)   
 [C + + 偵錯工具設定的專案設定](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C # Debug 設定的專案設定](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic Debug 設定的專案設定](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [如何：建立和編輯設定](../ide/how-to-create-and-edit-configurations.md)   
 [偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
