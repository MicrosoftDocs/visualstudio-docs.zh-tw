---
title: 格式、C/C++、文字編輯器、選項 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662334"
---
# <a name="options-text-editor-cc-formatting"></a>選項、文字編輯器、C/C++、格式設定
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

讓您在使用 C 或 C++ 進行程式設計時，變更 [程式碼編輯器] 的預設行為。

 若要存取這個頁面，請在 [選項]**** 對話方塊的左窗格中依序展開 [文字編輯器]**** 和 [C/C++]****，然後按一下 [格式]****。

> [!NOTE]
> 在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置： 您所擁有的 Visual Studio 版本以及使用的設定會決定這些項目。 如需詳細資訊，請參閱 [Visual Studio 中的自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。

## <a name="cc-options"></a>C/C++ 選項
 **啟用自動快速諮詢工具提示** 啟用或停用快速資訊 IntelliSense 功能。

## <a name="inactive-code"></a>非現用程式碼
 **顯示非** 使用中的程式碼區塊由於宣告而非使用中的程式碼 `#ifdef` 會以不同方式以色彩標示，以協助您進行識別。

 **停用非使用中程式碼不透明度** 非作用中的程式碼可以使用色彩而非透明度來識別。

 非使用中程式**代碼不透明度百分比**您可以自訂非使用中程式碼區塊的不透明度程度。

## <a name="indentation"></a>縮排
 **縮排大括弧** 您可以設定在開始程式碼區塊（例如，函式或迴圈）後按下 ENTER 時，如何對齊括弧 `for` 。 括號可以對齊程式碼區塊的第一個字元或是縮排。

 索引標籤**上的自動縮排**您可以設定在按下 TAB 鍵時，在目前的程式程式碼上發生什麼事。 程式碼行會縮排，或是會插入定位點。

## <a name="miscellaneous"></a>其他
 **列舉工作清單視窗中的批註** 編輯器可以掃描開啟的原始程式檔，以取得批註中的預設文字。 它會在 [工作清單]**** 視窗中為找到的任何關鍵字建立項目。

 **反白顯示相符的權杖** 當游標位於大括弧旁時，編輯器可以反白顯示相符的括弧，讓您可以更輕鬆地查看包含的程式碼。

## <a name="outlining"></a>大綱
 **當檔案開啟時進入大綱模式** 當您將檔案帶入文字編輯器時，您可以啟用大綱功能。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。 選取這個選項後，在您開啟檔案時將會啟用大綱功能。

 **#Pragma 區域區塊的自動大綱** 選取此選項時，會啟用 [pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) 指示詞的自動大綱。 這可讓您在大綱模式下展開或摺疊 Pragma 區域區塊。

 **語句區塊的自動大綱** 選取此選項時，會針對下列語句結構啟用自動大綱：

- [如果-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [switch 語句 (c + +) ](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [while 語句 (c + +) ](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>另請參閱
 [使用 IntelliSense](../../ide/using-intellisense.md)的[[一般]、[環境]、[選項] 對話方塊](../../ide/reference/general-environment-options-dialog-box.md)
