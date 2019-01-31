---
title: 使用 Visual C++ 程式碼 (類別設計工具) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90f0c73abb33a2da9c2735bcbc16b5559437bc65
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765008"
---
# <a name="working-with-visual-c-code-class-designer"></a>使用 Visual C++ 程式碼 (類別設計工具)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

類別設計工具會顯示名為「類別圖表」的視覺化設計介面，以視覺表示法提供專案中的程式碼項目。 您可以使用類別圖表來設計和視覺化類別和專案中的其他類型。  
  
 類別設計工具支援下列 C++ 程式碼元素：  
  
-   類別 (類似於 Managed 類別圖形，差別在於它可以有多個繼承關聯性)  
  
-   匿名類別 (會顯示類別檢視為匿名類型產生的名稱)  
  
-   範本類別  
  
-   結構  
  
-   列舉  
  
-   巨集 (會顯示巨集的後處理檢視)  
  
-   Typedef  
  
> [!NOTE]
>  這與 UML 類別圖不同，後者可在「模型專案」中建立。 如需詳細資訊，請參閱 [UML 類別圖表：參考資料](../modeling/uml-class-diagrams-reference.md)。  
  
## <a name="troubleshooting-type-resolution-and-display-issues"></a>類型解析與顯示問題的疑難排解  
  
### <a name="location-of-source-files"></a>原始程式檔的位置  
 類別設計工具不會追蹤原始程式檔的位置。 因此，如果您修改專案結構或移動專案中的原始程式檔，類別設計工具可能會遺失類型的追蹤 (特別是 typedef、基底類別或關聯類型的來源類型)。 您可能會收到錯誤，例如：**類別設計工具無法顯示這個類型**。 如果您收到錯誤訊息，請將已修改或重新配置的原始程式碼再次拖曳到類別圖表中，以重新顯示。  
  
### <a name="update-and-performance-issues"></a>更新和效能問題  
 在 Visual C++ 專案中，可能需要 30 到 60 秒，原始程式檔的變更才會出現在類別圖中。 此延遲也可能會導致類別設計工具擲回錯誤：**選取範圍中找不到任何類型**。 如果您收到這類錯誤，請在錯誤訊息中按一下 [取消]，並等候程式碼項目出現在 [類別檢視] 中。 執行這項操作後，類別設計工具即應能夠顯示類型。  
  
 如果類別圖未以您在程式碼中所做的變更進行更新，您可能需要關閉圖表，再加以重新開啟。  
  
### <a name="type-resolution-issues"></a>類型解析問題  
 類別設計工具無法解析類型的可能原因如下：  
  
- 類型所屬的專案或組件不是從包含類別圖的專案中參考的。 若要更正這個錯誤，請在包含類型的專案或組件中加入參考。 如需詳細資訊，請參閱[NIB 如何：新增或移除參考使用加入參考對話方塊](http://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
- 類型不在正確的範圍內，因此類別設計工具無法找到它。 請確定您的程式碼未遺漏 `using`、`imports` 或 `#include` 陳述式。 也請確定您未將該類型 (或相關類型) 從它最初建立所在的命名空間中移出。  
  
- 類型不存在 (或已標記為註解)。 若要更正這個錯誤，請確定您未將類型標記為註解或刪除類型。  
  
- 類型位於 #import 指示詞所參考的程式庫中。 可行的因應措施之一，是將產生的程式碼 (.tlh 檔) 手動加入至標頭檔中的 #include 指示詞。  
  
  關於類型解析問題，最常見的錯誤是：**找不到類別圖表 '\<element>'** 中一或多個圖形的程式碼。 此錯誤訊息不一定表示您的程式碼有錯誤。 它只是指出類別設計工具無法顯示您的程式碼。 您可以嘗試下列措施：  
  
- 確定類型存在。 確定您未在無意中將原始程式檔標記為註解或刪除原始程式檔。  
  
- 確定類別設計工具支援您所輸入的類型。 請參閱 [C++ 程式碼項目限制](#limitations)。  
  
- 嘗試解析類型。 類型所屬的專案或組件不是從包含類別圖的專案中參考的。 若要更正這個錯誤，請在包含類型的專案或組件中加入參考。 如需詳細資訊，請參閱[NIB 如何：新增或移除參考使用加入參考對話方塊](http://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)。  
  
- 確定類型位於正確的範圍內，讓類別設計工具能夠找到它。 確定程式碼未遺漏 `using`、`imports` 或 `#include` 陳述式。 也請確定您未將該類型 (或相關類型) 從它最初建立所在的命名空間中移出。  
  
### <a name="troubleshooting-other-error-messages"></a>其他錯誤訊息的疑難排解  
 您可以在 Microsoft Developer Network (MSDN) 公共論壇中尋求有關疑難排解錯誤和警告的協助。 請參閱 [Visual Studio 類別設計工具論壇](http://go.microsoft.com/fwlink/?linkid=160754)。  
  
##  <a name="limitations"></a> C++ 程式碼項目限制  
  
-   在載入 Visual C++ 專案時，類別設計工具會以唯讀方式運作。 您可以變更類別圖，但是您無法將類別圖中的變更存回至原始程式碼。  
  
-   類別設計工具僅支援原生 C++ 語意。 針對編譯為 Managed 程式碼的 Visual C++ 專案，類別設計工具只會視覺化屬於原生類型的程式碼元素。 因此，您可以將類別圖加入專案中，但是類別設計工具將不允許您視覺化 `IsManaged` 屬性設為 `true` 的元素 (也就是值類型和參考類型)。  
  
-   針對 Visual C++ 專案，類別設計工具只會讀取類型的定義。 例如，假設您將類型定義於標頭檔 (.h) 中，並將其成員定義於實作檔 (.cpp) 中。 如果您在實作檔 (.cpp) 上叫用「檢視類別圖」，類別設計工具將不會顯示任何項目。 另舉一例，如果您在使用 `#include` 陳述式的 .cpp 檔上叫用「類別圖檢視」，以包含其他檔案，但不包含任何實際類別定義，類別設計工具也不會顯示任何項目。  
  
-   IDL (.idl) 檔 (其中定義 COM 介面類型程式庫) 不會顯示在圖表中，除非它們編譯為原生 C++ 程式碼。  
  
-   類別設計工具不支援全域函式和變數。  
  
-   類別設計工具不支援等位。 這是配置的記憶體僅足以供等位的最大資料成員使用之類別的特殊類型。  
  
-   類別設計工具不會顯示基本資料類型，例如 `int` 和 `char`。  
  
-   如果專案沒有類型的正確參考，類別設計工具即不會顯示在目前的專案以外定義的類型。  
  
-   類別設計工具可以顯示巢狀類型，但不會顯示巢狀類型和其他類型之間的關係。  
  
-   類別設計工具無法顯示 void 類型或衍生自 void 類型的類型。  
  
## <a name="see-also"></a>請參閱  
 [設計和檢視類別與類型](../ide/designing-and-viewing-classes-and-types.md)   
 [使用類別和其他類型 (類別設計工具)](../ide/working-with-classes-and-other-types-class-designer.md)   
 [使用類別圖表 (類別設計工具)](../ide/working-with-class-diagrams-class-designer.md)   
 [設計類別和類型 (類別設計工具)](../ide/designing-classes-and-types-class-designer.md)   
 [類別設計工具錯誤的其他相關資訊](../ide/additional-information-about-class-designer-errors.md)   
 [類別設計工具中的 Visual C++ 類別](../ide/visual-cpp-classes-in-class-designer.md)   
 [類別設計工具中的 Visual C++ 結構](../ide/visual-cpp-structures-in-class-designer.md)   
 [類別設計工具中的 Visual C++ 列舉](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [類別設計工具中的 Visual C++ Typedef](../ide/visual-cpp-typedefs-in-class-designer.md)
