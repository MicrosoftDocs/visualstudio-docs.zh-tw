---
title: Visual Basic IntelliSense
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.Basic.IntelliSense
helpviewer_keywords:
- IntelliSense [Visual Basic]
- IntelliSense [Visual Studio], Visual Basic
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118de9ec05bcd5c56376376619bea0c5148d36ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594184"
---
# <a name="intellisense-for-visual-basic-code-files"></a>Visual Basic 程式碼檔案的 IntelliSense

Visual Basic 原始程式碼編輯器提供下列 IntelliSense 功能：

## <a name="syntax-tips"></a>語法提示

語法提示會顯示您正在鍵入的陳述式語法。 這非常適用於陳述式，例如 [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)。

## <a name="automatic-completion"></a>自動完成

- 完成各種關鍵字

     例如，如果您鍵入 `goto` 和一個空格，則 IntelliSense 會在下拉式功能表中顯示已定義的標籤清單。 其他支援的關鍵字包括 `Exit`、`Implements`、`Option` 和 `Declare`。

- 完成 `Enum` 和 `Boolean`

    當陳述式要參考列舉成員時，IntelliSense 會顯示 `Enum` 的成員清單。 當陳述式要參考 `Boolean` 時，IntelliSense 會顯示 true-false 下拉式功能表。

完成預設可以關閉，只要在 [Visual Basic]**** 資料夾取消選取 [一般]**** 屬性頁的 [自動列出成員]**** 即可。

您可以叫用 [列出成員]、[自動完成文字] 或**Alt** + **向右箭**號，手動叫用完成。 如需詳細資訊，請參閱[使用 IntelliSense](../ide/using-intellisense.md)。

## <a name="intellisense-in-zone"></a>IntelliSense in Zone

IntelliSense in Zone 可協助需要透過 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 部署應用程式，但受限於部分信任設定的 Visual Basic 開發人員。 此功能：

- 可讓您選擇應用程式的執行權限。

- 顯示 [列出成員] 中可用的所選區域 API，以及需要額外權限的無法使用 API。

如需詳細資訊，請參閱 [ClickOnce 應用程式的代碼啟用安全性](../deployment/code-access-security-for-clickonce-applications.md)。

## <a name="filtered-completion-lists"></a>篩選後的自動完成清單

在 Visual Basic 中，IntelliSense 完成清單有兩個接近清單底部的索引標籤控制項。 預設選取的 [通用]**** 索引標籤會顯示最常用來完成您所撰寫陳述式的項目。 [全部]**** 索引標籤會顯示所有可用於進行自動完成的項目，包含也在 [通用]**** 索引標籤上的項目。

## <a name="see-also"></a>另請參閱

- [使用 IntelliSense](../ide/using-intellisense.md)
