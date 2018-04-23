---
title: 語言服務及編輯器延伸模組入門 |Microsoft 文件
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
ms.openlocfilehash: 5e36f4a6b0f8cb37a5ede782c24c7593285b7705
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>開始使用語言服務與編輯器延伸模組
您可以使用編輯器延伸模組，將語言服務功能，例如，大綱、 括號對稱、 IntelliSense 和燈泡您自己的程式語言，或任何內容型別。 您也可以自訂的外觀和行為的 Visual Studio 編輯器，例如文字著色、 邊界、 裝飾和其他視覺化項目。 您也可以定義您自己的內容，類型，並指定的外觀和行為的文字檢視您的內容隨即出現。  
  
 若要開始撰寫編輯器延伸模組，使用的編輯器專案範本會安裝 Visual Studio SDK 的一部分。 Visual Studio SDK 是可下載的工具，可讓您更輕鬆地開發 Visual Studio 擴充功能，使用 Vspackage，或使用 Managed Extensibility Framework (MEF) 組。  
  
> [!NOTE]
>  如需有關 Visual Studio SDK 的詳細資訊，請參閱[Visual Studio SDK](../extensibility/visual-studio-sdk.md)。  
  
 我們建議您先了解下列概念和技術撰寫您自己的編輯器延伸模組之前。  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 和編輯器延伸模組  
 Visual Studio 編輯器使用者介面 (UI) 是使用 Windows Presentation Foundation (WPF) 來實作。 WPF 提供豐富的視覺效果和一致的程式設計模型與商務邏輯分隔的視覺效果的程式碼。 當您建立編輯器延伸模組時，您可以使用許多 WPF 項目與功能。 如需詳細資訊，請參閱[Windows Presentation Foundation](/dotnet/framework/wpf/index)。  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed 的 Extensibility Framework (MEF) 和編輯器延伸模組  
 在 Visual Studio 編輯器中會使用 Managed Extensibility Framework (MEF) 來管理其元件和副檔名。 MEF 也可讓開發人員更多輕鬆地建立類似 Visual Studio 主應用程式的擴充功能。 在這個架構中，您定義的延伸模組，根據 MEF 合約，並將它匯出為 MEF 元件組件。 主應用程式管理之元件部分，找到這些物件、 註冊，並確定它們會套用至正確的內容。  
  
> [!NOTE]
>  如需在編輯器中的 MEF 的詳細資訊，請參閱[在編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)。  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 編輯器中的擴充點和擴充功能  
 編輯器擴充點的 MEF 元件組件，您可以自訂及擴充。 在某些情況下您所實作介面並將它匯出加上正確的中繼資料擴充了擴充點。 在其他情況下，只宣告擴充功能，並將它匯出成特定類型。  
  
 下列是一些基本的編輯器延伸模組種類：  
  
-   邊界和捲軸  
  
-   Tags  
  
-   裝飾  
  
-   選項  
  
-   IntelliSense  
  
 如需編輯器的擴充點的詳細資訊，請參閱[語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)。  
  
## <a name="deploying-editor-extensions"></a>部署的編輯器延伸模組  
 在 Visual Studio 中，您會加入名為 source.extension.vsixmanifest 加入方案，建置方案的中繼資料檔案，然後將已知資料夾中的二進位檔案和資訊清單的副本將加入至 Visual Studio 部署編輯器延伸模組。 資訊清單檔案會定義有關擴充功能 （例如，名稱、 作者、 版本和內容類型） 的基本事項。 如需 VSIX 資訊清單檔案，以及如何部署延伸模組的詳細資訊，請參閱[傳送 Visual Studio 擴充功能](../extensibility/shipping-visual-studio-extensions.md)。  
  
 當您在電腦上安裝擴充功能時，包括資料夾的子資料夾，也是以 Visual Studio 中的二進位檔和資訊清單。  
  
> [!WARNING]
>  您不必擔心資訊清單及部署位置的詳細資訊，如果您使用其中一個隨附於 Visual Studio 擴充性範本編輯器。 範本會包含所需登錄及部署擴充功能的所有項目。  
  
## <a name="running-extensions-in-the-experimental-instance"></a>執行實驗執行個體中的擴充功能  
 藉由部署 （Windows Vista 和 Windows 7） 上的下列實驗資料夾中儲存的遊戲開發擴充功能時，您可以隔離您的工作版本的 Visual Studio:  
  
 *%LOCALAPPDATA%*\VisualStudio\10.0Exp\Extensions\\*公司*\\*ExtensionID*  
  
 其中*%LOCALAPPDATA%*是登入的使用者名稱，*公司*是擁有延伸模組的公司名稱和*ExtensionID*是擴充功能的識別碼。  
  
 當您部署延伸至實驗位置時，它會執行以偵錯模式。 Visual Studio 的第二個執行個體已啟動，且名為**Microsoft Visual Studio 實驗執行個體**。  
  
## <a name="managing-extensions"></a>管理擴充功能  
 Visual studio 的擴充功能會列示於**擴充功能和更新**(上**工具**功能表)。 如果您要測試擴充功能中的實驗執行個體，它列在**擴充功能和更新**在實驗執行個體，但並未列在開發執行個體。  
  
 如需詳細資訊，請參閱[尋找和使用 Visual Studio 延伸模組](../ide/finding-and-using-visual-studio-extensions.md)。  
  
## <a name="using-templates-to-create-editor-extensions"></a>使用範本來建立編輯器延伸模組  
 您可以使用編輯器範本來建立自訂分類器、 裝飾及邊界的 MEF 擴充功能。 有適用於 C# 和 Visual Basic 專案範本。 如需詳細資訊，請參閱[編輯器項目範本以建立擴充](../extensibility/creating-an-extension-with-an-editor-item-template.md)。  
  
 您也可以使用 VSIX 專案範本建立擴充功能。 此範本提供部署任何種類的延伸模組，並包含 source.extension.vsixmanifest 檔案、 必要的組件參考和專案檔，其中包含可讓您部署建置工作所需的項目延伸模組。 如需詳細資訊，請參閱[VSIX 專案範本](../extensibility/vsix-project-template.md)。  
  
 您也可以建立編輯器 MEF 元件從 Visual Studio 封裝擴充功能。 下列逐步解說，如需詳細資訊，請參閱：  
  
-   [逐步解說︰搭配編輯器擴充功能使用 Shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [逐步解說︰搭配編輯器擴充功能使用快速鍵](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>另請參閱  
 [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)