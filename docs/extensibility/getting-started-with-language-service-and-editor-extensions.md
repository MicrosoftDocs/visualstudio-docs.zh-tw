---
title: Getting Started with 語言服務及編輯器擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c07d2f374890d6a87b5fe45304d098acfb05065b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498376"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>語言服務及編輯器擴充功能入門
若要將語言服務功能，例如大綱、 括號對稱、 IntelliSense 和燈泡，加入您自己的程式設計語言或任何內容類型，您可以使用編輯器延伸模組。 您也可以自訂的外觀和行為的 Visual Studio 編輯器，例如色彩標示、 邊界、 裝飾和其他視覺元素的文字。 您也可以定義您自己的內容的類型，並指定的外觀和行為，您的內容會出現的文字檢視。  
  
 若要開始撰寫編輯器延伸模組，使用已安裝 Visual Studio SDK 的一部分的編輯器專案範本。 Visual Studio SDK 是可下載的工具，可讓您更輕鬆地使用 Vspackage，或使用 Managed Extensibility Framework (MEF) 開發 Visual Studio 擴充功能，一組。  
  
> [!NOTE]
>  如需有關 Visual Studio SDK 的詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
 我們建議您先了解下列概念和技術撰寫您自己的編輯器延伸模組之前。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>將 Windows Presentation Foundation (WPF) 和編輯器延伸模組  
 Visual Studio 編輯器使用者介面 (UI) 是使用 Windows Presentation Foundation (WPF) 來實作。 WPF 提供豐富的視覺效果和一致的程式設計模型與商務邏輯分隔的視覺效果，程式碼。 當您建立編輯器延伸模組時，您可以使用許多 WPF 項目和功能。 如需詳細資訊，請參閱 < [Windows Presentation Foundation](/dotnet/framework/wpf/index)。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>將 Managed Extensibility Framework (MEF) 和編輯器延伸模組  
 Visual Studio 編輯器會使用 Managed Extensibility Framework (MEF) 來管理其元件和延伸模組。 MEF 也可讓開發人員輕鬆地建立主應用程式，例如 Visual Studio 的擴充功能。 在此架構中，您可以定義根據 MEF 合約的延伸模組，並將它匯出為 MEF 元件組件。 主應用程式管理之元件部分，找到這些物件、 註冊，並確保它們會套用至正確的內容。  
  
> [!NOTE]
>  如需在編輯器中的 MEF 的詳細資訊，請參閱[編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 編輯器擴充點和擴充功能  
 編輯器擴充點的 MEF 元件部分，您可以自訂及擴充。 在某些情況下您會藉由實作介面，並將它匯出加上正確的中繼資料擴充擴充點。 在其他情況下，只是宣告的擴充功能，並將它匯出為特定類型。  
  
 以下是一些基本的編輯器延伸模組類型：  
  
-   邊界和捲軸  
  
-   Tags  
  
-   裝飾  
  
-   選項  
  
-   IntelliSense  
  
 如需有關編輯器擴充點的詳細資訊，請參閱[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)。  
  
## <a name="deploying-editor-extensions"></a>部署的編輯器延伸模組  
 在 Visual Studio 中，您必須部署編輯器擴充功能藉由新增名為的中繼資料檔案*source.extension.vsixmanifest*到解決方案、 建置方案時，，然後再將已知資料夾中的 的副本的二進位檔和資訊清單Visual studio。 資訊清單檔案會定義有關擴充功能 （例如名稱、 作者、 版本和類型的內容） 的基本事項。 如需 VSIX 資訊清單檔案，以及如何部署擴充功能的詳細資訊，請參閱[出貨的 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
 當您在電腦上安裝擴充功能時，請在資料夾的子資料夾，也是以 Visual Studio 中包含的二進位檔和資訊清單。  
  
> [!WARNING]
>  您不必擔心資訊清單和部署位置的詳細資料，如果您使用其中一個隨附於 Visual Studio 擴充性範本編輯器。 範本會包含所需登錄及部署擴充功能的所有項目。  
  
## <a name="run-extensions-in-the-experimental-instance"></a>執行實驗的執行個體中的擴充功能  
 藉由部署 （在 Windows Vista 和 Windows 7） 的下列實驗性資料夾中儲存的遊戲開發擴充功能時，您可以隔離您的 Visual Studio 版本：  
  
 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensions\\{公司}\\{ExtensionID}*  
  
 其中 *%LOCALAPPDATA%* 的身分登入的使用者名稱*公司*是公司擁有的延伸模組的名稱並*ExtensionID*是擴充功能的識別碼。  
  
 當您部署延伸模組的實驗性的位置時，它會在偵錯模式中執行。 Visual Studio 的第二個執行個體已啟動，且名為**Microsoft Visual Studio 實驗執行個體**。  
  
## <a name="manage-extensions"></a>管理擴充功能  
 Visual studio 的延伸模組都會列入**擴充功能和更新**(在**工具**功能表)。 如果您要測試擴充功能中的實驗執行個體，它會列於**擴充功能和更新**中實驗的執行個體，但未列於開發執行個體。  
  
 如需詳細資訊，請參閱 <<c0> [ 尋找及使用 Visual Studio 擴充功能](../ide/finding-and-using-visual-studio-extensions.md)。  
  
## <a name="use-templates-to-create-editor-extensions"></a>使用範本來建立編輯器延伸模組  
 您可以使用編輯器範本來建立自訂的分類器、 程式碼，在裝飾和邊界的 MEF 擴充功能。 有 C# 和 Visual Basic 專案範本。 如需詳細資訊，請參閱 <<c0> [ 使用編輯器項目範本建立擴充功能](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
 您也可以使用 VSIX 專案範本建立擴充功能。 此範本提供部署任何類型的延伸模組，並包含所需的項目*source.extension.vsixmanifest*檔案、 必要的組件參考和專案檔，其中包含組建工作可讓您部署延伸模組。 如需詳細資訊，請參閱 < [VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
 您也可以建立編輯器的 MEF 元件從 Visual Studio 封裝擴充功能。 下列逐步解說，如需詳細資訊，請參閱：  
  
-   [逐步解說： 搭配編輯器擴充功能使用 shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [逐步解說： 搭配編輯器擴充功能使用攠摝坫](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)