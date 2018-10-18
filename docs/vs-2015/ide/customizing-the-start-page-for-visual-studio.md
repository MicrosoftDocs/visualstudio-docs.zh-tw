---
title: 自訂適用於 Visual Studio 的起始頁 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
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
caps.latest.revision: 48
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ece49968c4a887e89f91feb83fae3de23aa2c282
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211480"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>自訂 Visual Studio 的起始頁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用幾個預設方式來自訂 Visual Studio 的起始頁，例如顯示 [開啟專案] 對話方塊或開啟最近載入的方案。 您也可以顯示自訂起始頁，這是一個在工具視窗中執行的 Windows Presentation Foundation (WPF) XAML 頁面，並且可以執行 Visual Studio 的內部命令。  
  
## <a name="customizing-the-default-start-page"></a>自訂預設起始頁  
  
1.  在功能表列上選擇 [工具] 、[選項] 。  
  
2.  展開 [環境]，然後選擇 [啟動]。  
  
3.  在 [啟動時] 清單中，選擇您要自訂的項目。  
  
## <a name="show-a-custom-start-page"></a>顯示自訂起始頁  
  
1.  使用下列其中一種方式來安裝自訂起始頁：  
  
    -   從 [Visual Studio 組件庫](http://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=start%20page)、其他網站或近端內部網路上的網頁來進行安裝。  
  
        > [!NOTE]
        >  如果您喜歡舊版 Visual Studio 的頁面，則可以使用 Visual Studio SDK 來升級頁面。 請參閱[如何： 升級 Visual Studio 自訂起始頁](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md)。  
  
         開啟.vsix 檔案，其中包含自訂起始頁，或複製並貼到起始頁檔案 **%USERPROFILE%documents\visual Studio 2015\StartPages**您電腦上的資料夾。  
  
    -   如果您已安裝 Visual Studio SDK，請建立您自己的起始頁。  
  
         請參閱[建立您自己的起始頁](../misc/creating-your-own-start-page.md)。  
  
2.  在功能表列上選擇 [工具] 、[選項] 。  
  
3.  展開 [環境]，然後選擇 [啟動]。  
  
4.  在 [自訂起始頁] 清單中，選擇您要的頁面。  
  
> [!NOTE]
>  如果自訂起始頁中的錯誤導致 Visual Studio 當掉，請以安全模式啟動 Visual Studio，然後設定它使用預設起始頁。 請參閱 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [建立您自己的起始頁](../misc/creating-your-own-start-page.md)



