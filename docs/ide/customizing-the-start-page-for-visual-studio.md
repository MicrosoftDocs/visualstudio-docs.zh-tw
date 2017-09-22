---
title: "自訂 Visual Studio 的起始頁 | Microsoft Docs"
ms.custom: 
ms.date: 02/01/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 102091f8214b822a5b6be1c93f913d6ddbcd8d9b
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---
# <a name="customize-the-start-page-for-visual-studio"></a>自訂 Visual Studio 的起始頁
您可以使用幾個預設方式來自訂 Visual Studio 的起始頁，例如顯示 [開啟專案] 對話方塊或開啟最近載入的方案。 您也可以顯示自訂起始頁，這是一個在工具視窗中執行的 Windows Presentation Foundation (WPF) XAML 頁面，並且可以執行 Visual Studio 的內部命令。  

## <a name="customize-the-default-start-page"></a>自訂預設起始頁  

1.  在功能表列上選擇 [工具] 、[選項] 。  

2.  展開 [環境]，然後選擇 [啟動]。  

3.  在 [啟動時] 清單中，選擇您要自訂的項目。  

## <a name="show-a-custom-start-page"></a>顯示自訂起始頁  

1.  使用下列其中一種方式來安裝自訂起始頁：  

    -   從 [Visual Studio 組件庫](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page)、其他網站或近端內部網路上的網頁來進行安裝。  

        開啟某個含有自訂起始頁的 .vsix 檔，或複製起始頁檔案並貼到電腦上的 **%USERPROFILE% \My Documents\Visual Studio 2017\StartPages** 資料夾中。  

    -   如果您已安裝 Visual Studio SDK，請建立您自己的起始頁。  

         請參閱[建立自訂起始頁](../extensibility/creating-a-custom-start-page.md)。  

2.  在功能表列上選擇 [工具] 、[選項] 。  

3.  展開 [環境]，然後選擇 [啟動]。  

4.  在 [自訂起始頁] 清單中，選擇您要的頁面。  

> [!NOTE]
>  如果自訂起始頁中的錯誤導致 Visual Studio 當掉，請以安全模式啟動 Visual Studio，然後設定它使用預設起始頁。 請參閱 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。  

## <a name="see-also"></a>請參閱  
 [將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)   

