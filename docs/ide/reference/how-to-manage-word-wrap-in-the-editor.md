---
title: 自動換行
description: 瞭解如何在程式碼編輯器中開啟和關閉 [自動換行] 選項。
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 57e218dadfe04d8cad034f2638ffefb9346e5a41
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894591"
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>如何：管理編輯器中的自動換行

您可以設定和清除 [自動換行] 選項。 設定這個選項時，過長的行超出目前程式碼編輯器視窗寬度的部分會顯示在下一行。 清除這個選項時，例如，為了方便使用行號，您可以捲動到右邊以看到過長行的結尾。

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 如 Visual Studio for Mac，請參閱 [來源編輯器：自動換行](/visualstudio/mac/source-editor#word-wrap)。

## <a name="to-set-word-wrap-preferences"></a>設定自動換行喜好設定

1. 在 [工具] 功能表上，選取 [選項]。

2. 在 [文字編輯器] 資料夾中，選擇 [所有語言] 子資料夾中的 [一般] 選項，全域設定這個選項。

     — 或者—

     選擇您進行程式設計所用語言子資料夾中的 [一般] 選項。

3. 在 [設定] 下，選取或清除 [自動換行] 選項。

     選取 [自動換行] 選項時，會啟用 [顯示自動換行的視覺化圖像] 選項。

4. 如果您想要在過長的行換行到第二行之處顯示傳回箭號指標，請選取 [顯示自動換行的視覺化圖像] 選項。 如果您不想顯示指示器箭號，請清除這個選項。

    > [!NOTE]
    > 這些提醒箭頭不會新增到程式碼：僅供顯示之用。

## <a name="known-issues"></a>已知問題

如果您很熟悉 Notepad++、Sublime Text 或 Visual Studio Code 中的自動換行，請留意 Visual Studio 與其他編輯器執行方式不同而產生的問題：

* [按三下無法選取整行](https://developercommunity.visualstudio.com/content/problem/268989/triple-click-doesnt-select-whole-line-when-word-wr.html)
* [按兩下 End 鍵不會將由標移到行的結尾](https://developercommunity.visualstudio.com/content/problem/138274/pressing-end-key-twice-should-move-cursor-to-end-o.html)

## <a name="see-also"></a>另請參閱

- [程式碼編輯器的功能](../../ide/writing-code-in-the-code-and-text-editor.md)
