---
title: 如何：設定 IDE 協助工具選項
description: 了解如何在 Visual Studio 中設定協助工具選項，使其整合式開發環境 (IDE) 更便於每個人使用，包括視力不佳而無法閱讀，以及靈活度有限而難以書寫的人士。
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d7cc99747571feb5b443f10355d867da7c22f44
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952911"
---
# <a name="how-to-set-ide-accessibility-options"></a>如何：設定 IDE 協助工具選項

Visual Studio 包含功能，可讓視力障礙人士更容易閱讀，讓靈活度有限的人士更容易書寫。 例如，您可以變更編輯器中的文字大小與色彩、變更工具列上的文字與按鈕大小，以及變更設定以協助您完成函式或陳述式。

此外，Visual Studio 支援 Dvorak 鍵盤配置，此配置可讓最常按的字元更容易存取。 您也可以自訂 Visual Studio 中可用的預設鍵盤快速鍵。 如需詳細資訊，請參閱[識別及自訂鍵盤快速鍵](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與此處所描述的不同。 若要變更您的設定，請在 [工具] 功能表上選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱[重設設定](../environment-settings.md#reset-settings)。

::: moniker range="vs-2017"

> [!TIP]
> 若要深入了解最新的協助工具更新，請參閱 [Visual Studio 2017 15.3 版中的協助工具改善](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) \(英文\) 部落格文章。

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>編輯器、對話方塊和工具視窗

根據預設，Visual Studio 中的對話方塊和工具視窗使用與作業系統相同的字型大小和色彩。 IDE 框架、對話方塊、工具列和工具視窗的色彩設定，是以色彩配置為基礎：淡或暗。 您可以在 [選項] 對話方塊中變更目前的色彩主題 [： [環境 > 一般]](../../ide/reference/general-environment-options-dialog-box.md)。

您也可以在編輯器的 [程式碼] 檢視中顯示快顯視窗。 這些視窗可以提示您目前物件上的可用成員和參數，以便完成函式或陳述式。 如果您不方便鍵入，這些視窗會很有用。 不過，它們會干擾程式碼編輯器中的焦點，可能會對某些使用者造成問題。

下面提供關閉快顯視窗的方式：

1. 從 [工具]  功能表選擇 [選項] 。

1. 選擇 **文字編輯器**  >  **所有語言**  >  **一般**。

1. 清除 [自動列出成員] 與 [參數資訊] 核取方塊。

您可以在整合式開發環境 (IDE) 中重新排列視窗，以符合您的工作方式。 您可以停駐、浮動、隱藏或自動隱藏每個工具視窗。 如需如何變更視窗配置的詳細資訊，請參閱[自訂視窗配置](../../ide/customizing-window-layouts-in-visual-studio.md)。

### <a name="change-the-size-of-text"></a>變更文字大小

您可以為以文字為基礎的工具視窗變更設定，例如 [命令]，例如 [命令] 視窗、[即是運算] 視窗與 [輸出] 視窗，方式是使用 [工具] > [選項] > [環境] > [字型和色彩]。

在 [顯示設定] 下拉式清單中選取 [所有文字工具視窗] 時，預設值會列為 [項目前景] 和 [項目背景] 下拉式清單中的 [預設]。 選擇 [自訂] 按鈕以變更這些設定。

您也可以在編輯器中變更文字顯示方式的設定。 方法如下。

1. 從 [工具]  功能表選擇 [選項] 。

1. 選擇 **環境** 字型  >  **和色彩**。

1. 在 [顯示設定] 下拉式功能表上選取選項。

    若要變更編輯器中文字的字型大小，請選擇 [文字編輯器]。

    若要變更以文字為基礎之工具視窗中的文字字型大小，請選擇 [所有文字工具視窗]。

    若要變更編輯器中工具提示文字的字型大小，請選擇 [編輯器工具提示]。

    若要變更陳述式完成快顯視窗中文字的字型大小，請選擇 [陳述式完成]。

1. 從 [顯示項目]，選取 [純文字]。

1. 在 [字型] 中，選取新的字型類型。

1. 在 [大小] 中，選取新的字型大小。

    > [!TIP]
    > 若要重設以文字為基礎之工具視窗和編輯器的文字大小，請選擇 [使用預設值]。

7. 選擇 [確定]。

### <a name="change-the-colors-that-are-used-in-the-ide"></a>變更 IDE 中使用的色彩

您可以選擇變更編輯器中文字、邊界指標、空白字元和程式碼項目的預設色彩。 方法如下。

1. 從 [工具]  功能表選擇 [選項] 。

1. 在 [環境] 資料夾中選擇 [字型和色彩]。

1. 在 [顯示設定] 中，選擇 [文字編輯器]。

1. 從 [顯示項目]，選取您要變更其顯示的項目，例如 [純文字]、[指示區邊界]、[可見的空白字元]、[HTML 屬性名稱] 或 [XML 屬性]。

1. 從下列選項選取顯示設定：[項目前景]、[項目背景] 和 [粗體]。

1. 選擇 [確定]。

> [!TIP]
> 若要對您作業系統上的所有應用程式視窗使用高對比色彩，請按 **左 Alt**+ + **左移** + **PrtScn**。 若 Visual Studio 已開啟，請關閉並重新開啟它以完全實作高對比色彩。

## <a name="toolbars"></a>工具列

若要改善工具列的可用性和協助工具，您可以為工具列按鈕新增文字。

### <a name="to-assign-text-to-toolbar-buttons"></a>將文字指派給工具列按鈕

1. 從 [工具] 功能表選擇 [自訂]。

1. 在 [自訂] 對話方塊中，選取 [命令] 索引標籤。

1. 選取 [ **工具列**]，然後選擇包含您想要顯示文字之按鈕的工具列名稱。

1. 在清單中，選取您想要變更的命令。

1. 選擇 [修改選取項目]。

1. 選擇 [影像和文字]。

### <a name="to-modify-the-displayed-text-in-a-button"></a>修改按鈕的顯示文字

1. 重新選取 [修改選取項目]。

1. 在相鄰 [名稱] 處，提供選取按鈕的新標題。

## <a name="see-also"></a>另請參閱

* [Visual Studio 的協助工具功能](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Visual Studio for Mac 的協助工具](/visualstudio/mac/accessibility/)
* [設計可存取應用程式的資源](../../ide/reference/resources-for-designing-accessible-applications.md)
