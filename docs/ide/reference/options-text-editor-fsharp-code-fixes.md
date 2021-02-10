---
title: 選項、文字編輯器、F#、程式碼修正
description: '瞭解如何使用 F # 區段中的程式碼修正頁面，來指定可協助識別程式碼錯誤和提供解決方案的設定。'
ms.custom: SEO-VS-2020
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.F%2523.Code_Fixes
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ca1b3816786ab611af8acb1cb99eea406ca6ad45
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943948"
---
# <a name="options-text-editor--f--code-fixes"></a>選項：文字編輯器 > F # > 程式碼修正

使用 [程式碼修正] 選項頁面來指定可協助找出程式碼錯誤並提供解決方案的設定。 若要存取此選項頁面，請選擇 [**工具**  >  **選項**]，然後選擇 [**文字編輯器**]  >  **F #**  >  **程式碼修正**。

## <a name="code-fixes"></a>程式碼修正

- **簡化名稱 (移除不必要的限定詞)**

  如果選取此核取方塊，則在不需要限定詞時會簡化完整名稱，例如經常使用的命名空間的成員。

- **一律將 open 陳述式放在最上層**

  如果選取此核取方塊並在程式碼中輸入 `open` 陳述式，則會將其置於最上層。

- **移除未使用的 open 陳述式**

  如果選取此核取方塊，則會針對未使用的 `open` 陳述式分析文件，且會顯示[快速控制項目](../quick-actions.md)燈泡，其具有移除所有未使用 `open` 陳述式的動作。

- **分析並建議修正未使用的值**

  如果選取此核取方塊，則工具會辨識程式碼中未使用的值。 然後，如果將滑鼠暫留在未使用的值上，它會建議您使用該值的方法。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
- [尋找 CodeLens 的程式碼變更和其他記錄](../../ide/find-code-changes-and-other-history-with-codelens.md)
