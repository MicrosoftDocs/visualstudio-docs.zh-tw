---
title: 開始使用語言服務及編輯器擴充功能
description: 瞭解如何將語言服務功能加入至任何內容類型，以及自訂 Visual Studio 編輯器的外觀和行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 471acaef0145b3bf1a73925b42e17a6343439ea2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994390"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>開始使用語言服務及編輯器擴充功能

您可以使用編輯器延伸模組，將語言服務功能（例如大綱、括弧對稱、IntelliSense 和 light 燈泡）新增至您自己的程式設計語言或任何內容類型。 您也可以自訂 Visual Studio 編輯器的外觀和行為，例如文字著色、邊界、裝飾和其他視覺元素。 您也可以定義自己的內容類型，並指定內容顯示所在文字視圖的外觀和行為。

 若要開始撰寫編輯器延伸模組，請使用安裝為 Visual Studio SDK 一部分的編輯器專案範本。 Visual Studio SDK 是一組可下載的工具，可讓您更輕鬆地開發 Visual Studio 擴充功能，方法是使用 Vspackage 或使用 Managed Extensibility Framework (MEF) 。

> [!NOTE]
> 如需 Visual Studio SDK 的詳細資訊，請參閱 [VISUAL STUDIO SDK](../extensibility/visual-studio-sdk.md)。

 在您撰寫自己的編輯器延伸模組之前，建議您先瞭解下列概念和技術。

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 和編輯器延伸模組

 Visual Studio 編輯器使用者介面 (UI) 是使用 Windows Presentation Foundation (WPF) 來執行。 WPF 提供豐富的視覺效果體驗和一致的程式設計模型，可將程式碼的視覺層面與商務邏輯分開。 當您建立編輯器延伸模組時，您可以使用許多 WPF 元素和功能。 如需詳細資訊，請參閱 [Windows Presentation Foundation](/dotnet/framework/wpf/index)。

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) 和編輯器延伸模組

 Visual Studio 編輯器會使用 Managed Extensibility Framework (MEF) 來管理其元件和延伸模組。 MEF 也可讓開發人員更輕鬆地建立主機應用程式（例如 Visual Studio）的擴充功能。 在此架構中，您會根據 MEF 合約定義擴充功能，並將它匯出為 MEF 元件部分。 主應用程式會藉由尋找元件元件、註冊它們，並確定它們已套用至正確的內容，來進行管理。

> [!NOTE]
> 如需編輯器中 MEF 的詳細資訊，請參閱 [編輯器中的 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)。

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 編輯器擴充點和延伸模組

 編輯器擴充點是您可以自訂和擴充的 MEF 元件部分。 在某些情況下，您會藉由執行介面並將其與正確的中繼資料一起匯出，來擴充擴充點。 在其他情況下，您只需宣告擴充功能，並將它匯出為特定類型。

 以下是一些基本類型的編輯器延伸模組：

- 邊界和捲軸

- 標籤

- 裝飾品

- 選項

- IntelliSense

  如需編輯器擴充點的詳細資訊，請參閱 [語言服務和編輯器延伸點](../extensibility/language-service-and-editor-extension-points.md)。

## <a name="deploying-editor-extensions"></a>部署編輯器延伸模組

 在 Visual Studio 中，您會將名為 *extension.vsixmanifest* 的中繼資料檔案新增至方案、建立方案，然後在已知要 Visual Studio 的資料夾中新增二進位檔案和資訊清單，以部署編輯器延伸模組。 資訊清單檔會定義關於延伸 (的基本事實，例如，名稱、作者、版本和內容類型) 。 如需有關 VSIX 資訊清單檔以及如何部署擴充功能的詳細資訊，請參閱 [寄送 Visual Studio 延伸](../extensibility/shipping-visual-studio-extensions.md)模組。

 當您在電腦上安裝延伸模組時，請將二進位檔和資訊清單包含在 Visual Studio 已知之資料夾的子資料夾中。

> [!WARNING]
> 如果您使用 Visual Studio 中包含的其中一個編輯器擴充性範本，則不需要擔心資訊清單和部署位置的詳細資料。 範本包含註冊和部署擴充功能所需的所有專案。

## <a name="run-extensions-in-the-experimental-instance"></a>在實驗實例中執行擴充功能

 您可以使用 Windows Vista 和 Windows 7) 上的下列實驗資料夾 (來部署擴充功能，以在開發延伸模組時，將 Visual Studio 的工作版本隔離：

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {ExtensionID}*

 其中 *% LOCALAPPDATA%* 是已登入使用者的名稱， *company* 是擁有此延伸模組的公司名稱，而 *ExtensionID* 則是延伸模組的識別碼。

 當您將延伸模組部署到實驗位置時，它會在「偵錯工具」模式中執行。 Visual Studio 的第二個實例已啟動，且名為 **Microsoft Visual Studio-實驗實例**。

## <a name="manage-extensions"></a>管理延伸模組

 Visual Studio 的延伸模組會列在 [**工具**] 功能表) 的 [**擴充功能和更新**] (中。 如果您要在實驗實例中測試擴充功能，它會列在實驗實例的 [ **擴充功能和更新** ] 中，但是不會列在開發實例中。

 如需詳細資訊，請參閱 [尋找和使用 Visual Studio 擴充](../ide/finding-and-using-visual-studio-extensions.md)功能。

## <a name="use-templates-to-create-editor-extensions"></a>使用範本建立編輯器延伸模組

 您可以使用編輯器範本來建立 MEF 延伸模組，以自訂分類器、裝飾和邊界。 C # 和 Visual Basic 專案都有範本。 如需詳細資訊，請參閱 [使用編輯器專案範本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

 您也可以使用 VSIX 專案範本來建立延伸模組。 此範本只會提供部署任何類型的延伸模組所需的專案，並包含 *extension.vsixmanifest* 檔案、必要的元件參考，以及包含可讓您部署擴充功能之組建工作的專案檔。 如需詳細資訊，請參閱 [VSIX 專案範本](../extensibility/vsix-project-template.md)。

 您也可以從 Visual Studio 套件擴充功能建立編輯器 MEF 元件。 如需詳細資料，請參閱下列逐步解說：

- [逐步解說：搭配編輯器延伸模組使用 shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [逐步解說：在編輯器延伸模組中使用快速鍵](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>另請參閱

- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
