---
title: 如何：管理編輯器中的自動換行
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36945273c58211865eccf464d810fb276598b665
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>如何：管理編輯器中的自動換行

您可以設定和清除 [自動換行] 選項。 設定這個選項時，過長的行超出目前程式碼編輯器視窗寬度的部分會顯示在下一行。 清除這個選項時，例如，為了方便使用行號，您可以捲動到右邊以看到過長行的結尾。

> [!NOTE]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../../ide/personalizing-the-visual-studio-ide.md)。

## <a name="procedure"></a>程序

### <a name="to-set-word-wrap-preferences"></a>設定自動換行喜好設定

1.  在 [工具] 功能表上，選取 [選項]。

2.  在 [文字編輯器] 資料夾中，選擇 [所有語言] 子資料夾中的 [一般] 選項，全域設定這個選項。

     — 或 —

     選擇您進行程式設計所用語言子資料夾中的 [一般] 選項。

3.  在 [設定] 下，選取或清除 [自動換行] 選項。

     選取 [自動換行] 選項時，會啟用 [顯示自動換行的視覺化圖像] 選項。

4.  如果您想要在過長的行換行到第二行之處顯示傳回箭號指標，請選取 [顯示自動換行的視覺化圖像] 選項。 如果您不想顯示指示器箭號，請清除這個選項。

    > [!NOTE]
    >  這些提醒箭頭不會新增到程式碼：它們僅供顯示之用。

## <a name="see-also"></a>另請參閱

- [自訂編輯器](../../ide/customizing-the-editor.md)
- [文字編輯器選項對話方塊](../../ide/reference/text-editor-options-dialog-box.md)
- [程式碼編輯器的功能](../../ide/writing-code-in-the-code-and-text-editor.md)