---
title: '使用 c + + 程式碼 (類別設計工具) '
description: 瞭解如何使用類別圖表來設計和視覺化專案中的 c + + 程式碼元素、類別和其他類型。
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- C++, Class Designer
- Class Designer, C++ support
- Class Designer, limitations
- Class Designer, tasks in C++
- C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 62993611ef7359095512f494767bbd3ea4cce5d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946575"
---
# <a name="work-with-c-code-in-class-designer"></a>使用類別設計工具中的 c + + 程式碼

[類別設計工具] 會顯示稱為「類別圖表」的視覺化設計介面，以視覺表示法提供專案中的程式碼項目。 您可以使用類別圖表來設計和視覺化類別和專案中的其他類型。

[類別設計工具] 支援下列 C++ 程式碼項目：

- 類別 (類似於 Managed 類別圖形，差別在於它可以有多個繼承關聯性)

- 匿名類別 (會顯示類別檢視為匿名類型產生的名稱)

- 範本類別

- 結構

- 列舉

- 巨集 (會顯示巨集的後處理檢視)

- Typedef

> [!NOTE]
> 這與 UML 類別圖不同，後者可在「模型專案」中建立。 如需詳細資訊，請參閱 [UML 類別圖表：參考](../../modeling/what-s-new-for-design-in-visual-studio.md)。

## <a name="troubleshoot-type-resolution-and-display-issues"></a>針對類型解析與顯示問題進行疑難排解

### <a name="location-of-source-files"></a>原始程式檔的位置

[類別設計工具] 不會追蹤原始程式檔的位置。 因此，如果您修改專案結構或移動專案中的原始程式檔，[類別設計工具] 可能會遺失類型的追蹤 (特別是 typedef、基底類別或關聯類型的來源類型)。 您可能會收到錯誤，例如：**類別設計工具無法顯示這個類型**。 如果您收到錯誤訊息，請將已修改或重新配置的原始程式碼再次拖曳到類別圖表中，以重新顯示。

### <a name="update-and-performance-issues"></a>更新和效能問題

若是 c + + 專案，來源檔案中的變更可能需要30到60秒，才能出現在類別圖表中。 此延遲也可能會導致 [類別設計工具] 擲回錯誤：**選取範圍中找不到任何類型**。 如果您收到這類錯誤，請在錯誤訊息中按一下 [取消]，並等候程式碼項目出現在 [類別檢視] 中。 執行這項操作後，[類別設計工具] 即應能夠顯示類型。

如果類別圖未以您在程式碼中所做的變更進行更新，您可能需要關閉圖表，再加以重新開啟。

### <a name="type-resolution-issues"></a>類型解析問題

[類別設計工具] 無法解析類型的可能原因如下：

- 類型所屬的專案或組件不是從包含類別圖的專案中參考的。 若要更正這個錯誤，請在包含類型的專案或組件中加入參考。 如需詳細資訊，請參閱 [管理專案中的參考](../managing-references-in-a-project.md)。

- 類型不在正確的範圍內，因此 [類別設計工具] 無法找到它。 請確定您的程式碼未遺漏 `using`、`imports` 或 `#include` 陳述式。 也請確定您未將該類型 (或相關類型) 從它最初建立所在的命名空間中移出。

- 類型不存在 (或已標記為註解)。 若要更正這個錯誤，請確定您未將類型標記為註解或刪除類型。

- 類型位於 #import 指示詞所參考的程式庫中。 可行的因應措施之一，是將產生的程式碼 (.tlh 檔) 手動加入至標頭檔中的 #include 指示詞。

- 確定 [類別設計工具] 支援您所鍵入的類型。 請參閱 [C++ 程式碼項目限制](#limitations-for-c-code-elements)。

您最有可能看到類型解析問題的錯誤是找不到 **類別圖 ' \<element> ' 中一或多個圖形的程式碼**。 此錯誤訊息不一定表示您的程式碼有錯誤。 它只是指出類別設計工具無法顯示您的程式碼。 您可以嘗試下列措施：

- 確定類型存在。 確定您未在無意中將原始程式檔標記為註解或刪除原始程式檔。

- 嘗試解析類型。 類型所屬的專案或組件不是從包含類別圖的專案中參考的。 若要更正這個錯誤，請在包含類型的專案或組件中加入參考。 如需詳細資訊，請參閱 [管理專案中的參考](../managing-references-in-a-project.md)。

- 確定類型位於正確的範圍內，讓類別設計工具能夠找到它。 確定程式碼未遺漏 `using`、`imports` 或 `#include` 陳述式。 也請確定您未將該類型 (或相關類型) 從它最初建立所在的命名空間中移出。

### <a name="troubleshoot-other-error-messages"></a>針對其他錯誤訊息進行疑難排解

您可以在 Microsoft Developer Network (MSDN) 公共論壇中尋求有關疑難排解錯誤和警告的協助。 請參閱 [Visual Studio 類別設計工具論壇](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsclassdesigner)。

## <a name="limitations-for-c-code-elements"></a>C++ 程式碼項目限制

- 載入 c + + 專案時，以唯讀方式 **類別設計工具** 函式。 您可以變更類別圖，但是您無法將類別圖中的變更存回至原始程式碼。

- [類別設計工具] 僅支援原生 C++ 語意。 針對編譯為 managed 程式碼的 c + + 專案， **類別設計工具** 只會視覺化屬於原生類型的程式碼專案。 因此，您可以將類別圖表新增至專案中，但是 [類別設計工具] 將不允許您視覺化 `IsManaged` 屬性設為 `true` 的項目 (也就是實值型別和參考型別)。

- 若是 c + + 專案， **類別設計工具** 只會讀取類型的定義。 例如，假設您將類型定義於標頭檔 (.h) 中，並將其成員定義於實作檔 (.cpp) 中。 如果您在實作檔 (.cpp) 上叫用「檢視類別圖表」，[類別設計工具] 將不會顯示任何項目。 另舉一例，如果您在使用 `#include` 陳述式的 .cpp 檔上叫用「檢視類別圖表」，以包含其他檔案，但不包含任何實際類別定義，[類別設計工具] 也不會顯示任何項目。

- IDL (.idl) 檔 (其中定義 COM 介面類型程式庫) 不會顯示在圖表中，除非它們編譯為原生 C++ 程式碼。

- [類別設計工具] 不支援全域函式和變數。

- [類別設計工具] 不支援等位。 這是配置的記憶體僅足以供等位的最大資料成員使用之類別的特殊類型。

- [類別設計工具] 不會顯示基本資料類型，例如 `int` 和 `char`。

- 如果專案沒有類型的正確參考，[類別設計工具] 即不會顯示在目前的專案以外定義的類型。

- [類別設計工具] 可以顯示巢狀類型，但不會顯示巢狀類型和其他類型之間的關聯性。

- [類別設計工具] 無法顯示無效類型或衍生自無效類型的類型。

## <a name="see-also"></a>另請參閱

- [設計和檢視類別與類型](designing-and-viewing-classes-and-types.md)
- [類別設計工具錯誤的其他相關資訊](additional-information-about-errors.md)
- [類別設計工具中的 c + + 類別](visual-cpp-classes.md)
- [類別設計工具中的 c + + 結構](visual-cpp-structures.md)
- [類別設計工具中的 c + + 列舉](visual-cpp-enumerations.md)
- [類別設計工具中的 c + + Typedef](visual-cpp-typedefs.md)
