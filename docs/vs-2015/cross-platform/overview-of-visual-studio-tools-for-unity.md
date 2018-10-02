---
title: Visual Studio Tools for Unity 概觀 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: bea1ce00cfae19954153fa994c10b2211be19806
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47499214"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Visual Studio Tools for Unity 概觀
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[的 Visual Studio Tools for Unity 概觀](https://docs.microsoft.com/visualstudio/cross-platform/overview-of-visual-studio-tools-for-unity)。  
  
  
在本節中，您將進一步了解 Visual Studio Tools for Unity 所提供的功能，及如何使用這些功能更有效率地使用 Unity。  
  
 透過 Visual Studio Tools for Unity (*VSTU*)，您可以在 C# 中使用 Visual Studio 來撰寫遊戲和編輯器指令碼，然後使用其強大的偵錯工具來尋找及修正錯誤。 最新版的 VSTU 包含 Unity ShaderLab 著色器語言的語法著色、更佳的偵錯工具視覺化，以及 MonoBehavior 精靈的改良式程式碼產生。 VSTU 也會將您的 Unity 專案檔案、主控台訊息和啟動遊戲的功能整合到 Visual Studio 中，以便您可以在撰寫程式碼時，花較少的時間來切換 Unity Editor。  
  
 請繼續閱讀，以進一步了解這些功能。  
  
## <a name="integration-with-unity"></a>與 Unity 整合  
 如果您必須一直在 Unity Editor 和 Visual Studio 之間來回切換，Visual Studio Tools for Unity 就稱不上是提升產能的好工具。 因此，Visual Studio Tools for Unity 讓您不需要離開 Visual Studio，就能輕鬆繼續工作。  
  
-   **Unity Project Explorer** 使用與 Unity Editor 相同的階層架構，在 Visual Studio 中顯示整個 Unity 專案。  
  
-   Unity 主控台整合會直接在 Visual Studio 錯誤視窗內，顯示 Unity 主控台的輸出。  
  
-   您不需要切換回 Unity，只要按 F5 鍵，就能從 Visual Studio 開始偵錯您的遊戲。  
  
## <a name="superior-debugging"></a>高階偵錯  
 不論是獨立執行或是在 Unity Editor 中執行，您都可以將 Visual Studio 的強大偵錯工具連接到 Unity 遊戲，對 C# 指令碼和 DLL 進行偵錯。 您可以使用預期可從 Visual Studio 取得的所有偵錯功能。  
  
-   中斷點，包括條件式中斷點。  
  
-   在監看式視窗中評估複雜的運算式。  
  
-   檢查及修改變數和引數的值。  
  
-   向下切入至複雜的物件和資料結構。  
  
 您甚至可以在網路上另一部機器正在執行 Unity 遊戲時，對遊戲進行偵錯。  
  
## <a name="productivity"></a>產能  
 除了 Visual Studio 撰寫及重構 C# 程式碼的既有產能之外，Visual Studio Tools for Unity 還提供額外的產能功能給 Unity 開發人員。  
  
-   Unity ShaderLab 語言的語法著色可協助您在錯誤變成 Bug 之前，在著色器中找出這些錯誤。 只要在 Visual Studio 中開啟 ShaderLab 檔案即可。  
  
-   MonoBehavior 精靈可讓您瀏覽 Unity 行為清單，並為您可能不熟悉的行為建立未定案程式碼。 按 CTRL+SHIFT+M。  
  
-   一旦您熟悉最常使用的 Unity 行為，Quick MonoBehavior 精靈便會將這些行為放在您可以隨時取得的位置。 按 CTRL+ALT+Q。  
  
-   從 Visual Studio 存取 Unity 文件。 請直接反白顯示您要了解的應用程式開發介面呼叫，然後按 CTRL+ALT+M、CTRL+H。  
  
-   使用鍵盤快速鍵存取上述所有功能和其他功能。  
  
## <a name="visual-studio-tools-for-unity-api"></a>Visual Studio Tools for Unity 應用程式開發介面  
 使用提供的應用程式開發介面自訂及擴充 Visual Studio Tools for Unity 的行為。  
  
-   Visual Studio Tools for Unity 會註冊記錄回呼，以便將 Unity 主控台串流至 Visual Studio。 如果您有記錄資訊的編輯器指令碼，您可以將這些指令碼插入相同的回呼，以將訊息傳送至 Visual Studio。 如需詳細資訊，請參閱「記錄回呼」範例。  
  
-   您可以使用 Unity 樣式回呼 ProjectFileGeneration，來變更 Visual Studio Tools for Unity 產生專案檔的方式。 如需詳細資訊，請參閱「產生專案檔」範例。  
  
## <a name="see-also"></a>另請參閱  
 [Unity 首頁 (英文)](http://unity3d.com)

