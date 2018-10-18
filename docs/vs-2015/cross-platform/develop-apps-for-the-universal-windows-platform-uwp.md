---
title: 開發適用於通用 Windows 平台 (UWP) 的應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 1235416a411935d811f3747fa5127cc395ef0f29
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287088"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>開發適用於通用 Windows 平台 (UWP) 的應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
透過通用 Windows 平台和單一 Windows 核心，您可以在從手機到桌上型電腦的任何 Windows 10 裝置上執行相同的應用程式。 您可以使用 Visual Studio 2015 和通用 Windows 應用程式開發工具，來建立這些通用 Windows 應用程式。  
  
 ![通用 Windows 平台](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 在 Windows 10 手機、Windows 10 桌上型電腦或 Xbox 上執行您的應用程式。 全部使用相同的應用程式套件！ 有了 Windows 10 單一整合核心，一個應用程式套件可以在所有平台上執行。 數個平台都有擴充功能 SDK，可供您加入應用程式以利用平台專屬行為。 例如，手機的擴充功能 SDK 會處理在 Windows 手機上按下返回鍵的行為。 如果您在專案中參考擴充功能 SDK，只要加入執行階段檢查，就能測試該平台是否可以使用這個 SDK。 因此，您可以針對每一個平台使用相同的應用程式套件！  
  
 **Windows Core 是什麼？**  
  
 這是第一次 Windows 在重整後擁有一個所有 Windows 10 平台通用的核心。 這個核心 (Core) 包含一個通用來源、一個通用 Windows 核心 (Kernel)、一個檔案 I/O 堆疊，還有一個應用程式模型。 針對 UI，只有一個 XAML UI 架構和一個 HTML UI 架構。 由於在不同的 Windows 10 裝置上執行應用程式變得很容易，因此您可以專注於建立絕佳的應用程式。  
  
 **通用 Windows 平台到底是什麼？**  
  
 它不過是合約和版本的集合。 該集合可讓您設定要執行應用程式的目標。 您不會再以作業系統為目標。 現在您會將應用程式的目標設為一個或多個裝置系列。 如需詳細資訊，請參閱此 [平台指南](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx)。  
  
## <a name="requirements"></a>需求  
 通用 Windows 應用程式開發工具隨附模擬器，可供您用來查看應用程式在不同裝置上的外觀。 如果您要使用這些模擬器，您需要在實體電腦上安裝這個軟體。 這部實體機器必須執行 Windows 8.1 (x64) Professional Edition (含) 以上版本，並具備支援用戶端 Hyper-V 和第二層位址轉譯 (SLAT) 的處理器。 如果在虛擬機器上安裝 Visual Studio，則無法使用模擬器。  
  
 以下是您需要的軟體清單：  
  
-   [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
-   [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725)。 請務必從選擇性功能清單中選取通用 Windows 應用程式開發工具。 如果沒有這些工具，您將無法建立通用應用程式。  
  
 安裝這個軟體之後，您也需要 [啟用 Windows 10 裝置](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) 進行開發。 (您不再需要取得每部 Windows 10 裝置的開發人員授權)。  
  
 **Windows 8.1 和 Windows 7 支援**  
  
 如果您選擇在非 Windows 10 平台上，使用 Visual Studio 2015 開發通用 Windows 應用程式，其限制如下：  
  
-   Windows 8.1：您無法在本機執行應用程式 (僅限在遠端 Windows 10 裝置上)。 您可以使用 Visual Studio 中的模擬器 (Emulator)，但無法使用模擬器 (Simulator)。  
  
-   Windows 7：您無法在本機執行應用程式 (僅限在遠端 Windows 10 裝置上)。 您無法使用 Visual Studio 中的模擬器 (Emulator 或 Simulator)。  
  
 如果您的開發平台為 Windows 10，則只能使用 XAML 設計工具。  
  
## <a name="universal-windows-apps"></a>通用 Windows 應用程式  
 從 C#、Visual Basic、C++ 或 JavaScript 中，選擇您慣用的開發語言，以 [建立適用於 Windows 10 的通用 Windows 應用程式](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10)。 或觀賞 [此快速入門影片](http://channel9.msdn.com/Series/ConnectOn-Demand/229)。  
  
 若您現有的 Windows 市集 8.1 應用程式、Windows Phone 8.1 應用程式或通用 Windows 應用程式是以 Visual Studio 2015 RC 所建立，請 [移轉這些現有的應用程式](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) ，以使用最新版的通用 Windows 平台。  
  
 建立通用 Windows 應用程式之後，您必須 [封裝您的應用程式](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) ，以在 Windows 10 裝置上進行安裝，或提交至 Windows 市集。

