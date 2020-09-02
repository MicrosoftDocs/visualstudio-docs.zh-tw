---
title: 自訂起始頁 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665843"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>自訂 Visual Studio 的起始頁
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用幾個預設方式來自訂 Visual Studio 的起始頁，例如顯示 [開啟專案]**** 對話方塊或開啟最近載入的方案。 您也可以顯示自訂起始頁，這是一個在工具視窗中執行的 Windows Presentation Foundation (WPF) XAML 頁面，並且可以執行 Visual Studio 的內部命令。

## <a name="customizing-the-default-start-page"></a>自訂預設起始頁

1. 在功能表列上選擇 [工具] ****、[選項] ****。

2. 展開 [環境]****，然後選擇 [啟動]****。

3. 在 [啟動時]**** 清單中，選擇您要自訂的項目。

## <a name="show-a-custom-start-page"></a>顯示自訂起始頁

1. 使用下列其中一種方式來安裝自訂起始頁：

    - 從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/)、其他網站，或近端內部網路上的網頁來進行安裝。

        > [!NOTE]
        > 如果您喜歡舊版 Visual Studio 的頁面，則可以使用 Visual Studio SDK 來升級頁面。 請參閱[如何：升級 Visual Studio 自訂起始畫面](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md)。

         開啟某個含有自訂起始頁的 .vsix 檔，或複製起始頁檔案並貼到電腦上的 **%USERPROFILE% \My Documents\Visual Studio 2015\StartPages** 資料夾中。

    - 如果您已安裝 Visual Studio SDK，請建立您自己的起始頁。

         請參閱[建立您自己的起始頁](../misc/creating-your-own-start-page.md)。

2. 在功能表列上選擇 [工具] ****、[選項] ****。

3. 展開 [環境]****，然後選擇 [啟動]****。

4. 在 [自訂起始頁]**** 清單中，選擇您要的頁面。

> [!NOTE]
> 如果自訂起始頁中的錯誤導致 Visual Studio 當掉，請以安全模式啟動 Visual Studio，然後設定它使用預設起始頁。 請參閱 [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md)。

## <a name="see-also"></a>另請參閱
 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [建立您自己的起始頁](../misc/creating-your-own-start-page.md)
