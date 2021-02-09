---
title: 設定 Visual Studio 深色主題並變更文字色彩
description: 瞭解如何將預設的 Visual Studio 色彩主題變更為深色模式，並在程式碼編輯器中變更字型色彩。
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb7c9bf04e5f38e5138eae6cf6254bb77bbd6230
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916061"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>如何：將 Visual Studio IDE 和編輯器個人化

在此操作說明文章中，我們將從預設的藍色主題，將 Visual Studio 色彩主題自訂為深色主題。 然後，我們會在程式碼編輯器中自訂兩個不同類型之文字的色彩。

::: moniker range="vs-2017"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)頁面免費進行安裝。

::: moniker-end

::: moniker range=">=vs-2019"

如果您尚未安裝 Visual Studio，請前往 [Visual Studio 下載](https://visualstudio.microsoft.com/downloads)頁面免費進行安裝。

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>設定 IDE 的色彩主題

Visual Studio 使用者介面的預設色彩佈景主題為 [藍色]。 讓我們將它變更為 [深色]。

1. 在功能表列上 (即 [檔案] 和 [編輯] 這類功能表列)，選擇 [工具] > [選項]。

1. 在 [**環境**  >  **一般** 選項] 頁面上，將 **色彩主題** 選取範圍變更為 [**深色**]，然後選擇 **[確定]**。

   整個 Visual Studio 開發環境 (IDE) 色彩佈景主題變更為 [深色]。

   ::: moniker range="vs-2017"

   ![深色佈景主題的 Visual Studio 2017](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![深色佈景主題的 Visual Studio 2019](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> 您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor) \(英文\) 安裝 **Visual Studio 色彩佈景主題編輯器**，以安裝額外的預先定義佈景主題。 安裝此工具之後，其他色彩主題會出現在 [ **色彩主題** ] 下拉式清單中。

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> 您可以從 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)安裝 **Visual Studio 色彩主題設計** 工具，以建立您自己的主題。

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>變更編輯器中的文字色彩

現在我們將自訂編輯器的部分文字色彩。 首先，讓我們建立新的 XML 檔案來查看預設色彩。

1. 從功能表 **欄選擇 [** 檔案新檔案]  >    >  ****。

1. 在 [新增檔案] 對話方塊中的 [一般] 類別下，選擇 [XML 檔案]，然後選擇 [開啟]。

1. 在包含 `<?xml version="1.0" encoding="utf-8"?>` 的行下方，貼上下列 XML。

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   請注意，行號是藍綠色，而 XML 屬性 (例如 `id="bk101"`) 是淺藍色。 我們要變更這些項目的文字色彩。

   ![XML 檔案的字型色彩](media/quickstart-personalize-xml-file.png)

1. 若要開啟 [選項] 對話方塊，請從功能表列中選擇 [工具] > [選項]。

1. 在 [環境] 底下，選擇 [字型和色彩] 類別。

   請注意，[顯示設定] 底下的文字為 [文字編輯器]&mdash; 這正是我們要的設定目標。 展開下拉式清單，看看您可以自訂字型和文字色彩的多個位置清單。

1. 若要變更行號文字的色彩，請在 [顯示項目] 清單中，選擇 [行號]。 在 [項目前景] 方塊中，選擇 [橄欖色]。

   ![[選項] 對話方塊、[字型和色彩] 類別](media/quickstart-personalize-line-number-color.png)

   某些語言具有其專屬特定字型和色彩設定。 如果您是 C++ 開發人員，而且想要變更用於函式的色彩，例如，您可以在 [顯示項目] 清單中尋找 [C++ 函式]。

1. 在結束對話方塊之前，讓我們也變更 XML 屬性的色彩。 在 [顯示項目] 清單中，向下捲動至 [XML 屬性] 並加以選取。 在 [項目前景] 方塊中，選擇 [淡黃綠色]。 選擇 [確定] 以儲存選取項目並關閉對話方塊。

   行號現在是橄欖色，而且 XML 屬性會是明亮的黃綠色。 如果您開啟其他檔案類型，例如 C++ 或 C# 程式碼檔案，您將看到行號也會以橄欖色顯示。

   ![使用新字型色彩的 XML 檔案](media/quickstart-personalize-xml-file-new-colors.png)

我們已探索在 Visual Studio 中自訂色彩的幾種方式。 我們希望您將探索 [ [**選項**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) ] 對話方塊中的其他自訂選項，以真正 Visual Studio 您自己的選項。

## <a name="see-also"></a>另請參閱

- [如何：在 Visual Studio 中變更字型、色彩和主題](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [如何：變更編輯器中的文字大小寫](../ide/how-to-change-text-case-in-the-editor.md)
- [Visual Studio IDE 概觀](../get-started/visual-studio-ide.md)
