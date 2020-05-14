---
title: 開始使用語言服務和編輯器擴展 |微軟文件
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
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711302"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>開始使用語言服務及編輯器延伸
您可以使用編輯器擴展將語言服務功能(如大綱、大括弧匹配、IntelliSense 和燈泡)添加到您自己的程式設計語言或任何內容類型。 您還可以自定義 Visual Studio 編輯器的外觀和行為,例如文本著色、邊距、修飾和其他可視元素。 您還可以定義自己的內容類型,並指定內容所在的文本視圖的外觀和行為。

 要開始編寫編輯器擴展,請使用作為可視化工作室 SDK 的一部分安裝的編輯器專案範本。 Visual Studio SDK 是一組可下載的工具,透過使用 VS 套件或使用託管擴充性框架 (MEF),可以更輕鬆地開發 Visual Studio 擴充。

> [!NOTE]
> 有關可視化工作室 SDK 的詳細資訊,請參閱[可視化工作室 SDK](../extensibility/visual-studio-sdk.md)。

 我們建議您在編寫自己的編輯器擴展之前瞭解以下概念和技術。

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows 示範基礎 (WPF) 與編輯器延伸
 可視化工作室編輯器使用者介面 (UI) 是透過使用 Windows 示範基礎 (WPF) 實現的。 WPF 提供了豐富的視覺體驗和一致的程式設計模型,將代碼的可視方面與業務邏輯分開。 建立編輯器擴展時,可以使用許多 WPF 元素和功能。 有關詳細資訊,請參閱[Windows 簡報資料基礎](/dotnet/framework/wpf/index)。

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>託管延伸性框架 (MEF) 與編輯器延伸
 可視化工作室編輯器使用託管擴展框架 (MEF) 來管理其元件和擴展。 MEF 還允許開發人員更輕鬆地為 Visual Studio 等主機應用程式創建擴展。 在此框架中,您可以根據 MEF 協定定義擴展,並將其匯出為 MEF 元件零件元件。 主機應用程式通過查找元件、註冊元件並確保它們應用於正確的上下文來管理元件部件。

> [!NOTE]
> 有關編輯器中的 MEF 的詳細資訊,請參考[編輯器中的託管擴充性框架](../extensibility/managed-extensibility-framework-in-the-editor.md)。

## <a name="visual-studio-editor-extension-points-and-extensions"></a>視覺化工作室編輯器擴充點和擴充
 編輯器擴展點是可以自定義和擴展的 MEF 元件元件。 在某些情況下,您可以通過實現介面並將其與正確的元數據一起導出來擴展擴展點。 在其他情況下,您只是聲明一個擴展並將其匯出為特定類型。

 以下是編輯器延伸的一些基本型態:

- 邊距與捲動條

- Tags

- 裝飾品

- 選項。

- IntelliSense

  有關編輯器延伸點的詳細資訊,請參考[語言服務和編輯器延伸點](../extensibility/language-service-and-editor-extension-points.md)。

## <a name="deploying-editor-extensions"></a>部署編輯器延伸
 在 Visual Studio 中,您可以透過向解決方案添加名為*source.擴展.vsixmanifest*的中繼資料檔來部署編輯器擴展,生成解決方案,然後在 Visual Studio 已知的資料夾中添加二進位檔案和清單的副本。 清單檔定義有關副檔名的基本事實(例如,名稱、作者、版本和內容類型)。 有關 VSIX 清單檔以及如何部署擴充的詳細資訊,請參閱[船舶可視化工作室擴展](../extensibility/shipping-visual-studio-extensions.md)。

 在電腦上安裝擴展時,將二進位檔和清單包含在 Visual Studio 已知的資料夾的子資料夾中。

> [!WARNING]
> 如果使用 Visual Studio 中包含的編輯器擴展範本之一,則不必擔心清單和部署位置的詳細資訊。 範本包含註冊和部署擴展所需的所有內容。

## <a name="run-extensions-in-the-experimental-instance"></a>在實驗實例中執行擴充
 在開發延伸時,您可以透過在以下實驗資料夾中(在 Windows Vista 和 Windows 7 上)部署該擴展來隔離工作版本的 Visual Studio:

 *[%本地應用資料%][VisualStudio]10.0Exp_擴展\\[公司\\] [擴展 ID]*

 *其中 %LOCALAPPDATA%* 是登入使用者的名稱,*公司*是擁有擴充名的公司的名稱,*擴展 ID*是擴充的 ID。

 將擴展部署到實驗位置時,它將在調試模式下運行。 視覺工作室的第二個實例啟動,並命名為**微軟視覺工作室-實驗實例**。

## <a name="manage-extensions"></a>管理延伸模組
 "扩展 **"和"更新**"(在 **"工具"** 功能表上)中列出了可視化工作室的擴展。 如果要在實驗實例中測試擴展,它將在實驗實例中的**擴展和更新**中列出,但在開發實例中未列出。

 有關詳細資訊,請參閱[尋找和使用可視化工作室擴展](../ide/finding-and-using-visual-studio-extensions.md)。

## <a name="use-templates-to-create-editor-extensions"></a>使用樣本建立編輯器延伸
 可以使用編輯器範本創建自定義分類器、修飾和邊距的 MEF 擴展。 C# 和可視化基本專案都有範本。 關於詳細資訊,請參考[使用編輯器項目樣本建立延伸](../extensibility/creating-an-extension-with-an-editor-item-template.md)。

 您還可以使用 VSIX 專案範本創建擴充。 此範本僅提供部署任何類型的延伸所需的元素,並包括*source.擴展.vsixmanifest*檔、所需的程式集引用以及包含允許您部署擴充的產生任務的專案檔。 有關詳細資訊,請參閱[VSIX 專案樣本](../extensibility/vsix-project-template.md)。

 您還可以從可視化工作室包擴展創建編輯器 MEF 元件。 有關詳細資訊,請參閱以下演練:

- [演練:使用具有編輯器延伸的 shell 命令](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [演練:使用帶有編輯器延伸的捷徑](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>另請參閱
- [語言服務及編輯器擴充點](../extensibility/language-service-and-editor-extension-points.md)
