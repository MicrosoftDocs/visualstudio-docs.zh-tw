---
title: 快速入門： C-C + + 的程式碼分析 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278477"
---
# <a name="quick-start-code-analysis-for-cc"></a>快速入門：C/C++ 程式碼分析
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以在 C 或 C++ 程式碼上定期執行程式碼分析，以改善您的應用程式品質。 這可協助您尋找常見的問題、良好的程式設計作法違規狀況，或偵測難以透過測試發現的缺失。 程式碼分析警告與編譯器錯誤和警告不同，因為程式碼分析會搜尋有效的特定程式碼模式，但仍然可以為您或使用您程式碼的其他人建立問題。  
  
## <a name="in-this-topic"></a>本主題內容  
  
- [設定專案的規則集](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [執行程式碼分析](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [分析和解決程式碼分析警告](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [隱藏程式碼分析警告](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [建立程式碼分析警告的工作項目](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [搜尋和篩選程式碼分析結果](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="configure-rule-sets-for-a-project"></a><a name="BKMK_ConfigureRuleSets"></a> 設定專案的規則集  
  
1. 在 **方案總管**中，開啟專案名稱的快捷方式功能表，然後選擇 [ **屬性**]。  
  
2. 下列是選用的步驟：  
  
    1. 在 [設定] 和 [**平臺**] 清單中，選擇 [組建設定 **] 和 [** 目標平臺]。  
  
    2. 根據預設，程式碼分析不會報告從外部工具自動產生的程式碼警告。 若要從產生的程式碼中查看警告，請清除 [ **隱藏產生** 的程式碼的結果] 核取方塊。  
  
        > [!NOTE]
        > 這個選項不會在表單和範本中出現錯誤和警告時，抑制來自產生的程式碼的程式碼分析錯誤和警告。 您可以同時檢視及維護表單或範本的原始程式碼。  
  
3. 若要在每次使用選取的設定建立專案時執行程式碼分析，請選取 [ **在組建上啟用 c/c + + 的程式碼分析** ] 核取方塊。 您也可以開啟 [**分析**] 功能表，然後選擇 [針對*專案名稱***執行程式碼分析**]，藉以手動執行程式碼分析。  
  
4. 在 [ **執行此規則集** ] 清單中，執行下列其中一項：  
  
    - 選擇想要使用的規則集。  
  
    - 選擇 **\<Browse...>** 指定不在清單中的現有自訂規則集。  
  
    - 定義自訂規則集。  
  
         如需詳細資訊，請參閱 [建立自訂規則集](../code-quality/creating-custom-code-analysis-rule-sets.md)。  
  
### <a name="standard-cc-rule-sets"></a>標準 C/C++ 規則集  
 Visual Studio 包含兩組標準的原生程式碼規則：  
  
|規則集|說明|  
|--------------|-----------------|  
|Microsoft 原生最小建議規則|此規則集的重點在於機器碼中最關鍵的問題，包括可能的安全性漏洞和應用程式損毀。 您應該在為原生專案建立的任何自訂規則集中，包含此規則集。|  
|Microsoft 原生建議規則|此規則集涵蓋廣泛的問題。 它在 Microsoft 原生最小建議規則中包含所有規則。|  
  
## <a name="run-code-analysis"></a><a name="BKMK_Run"></a> 執行程式碼分析  
 在專案屬性頁面的 [程式碼分析] 頁面上，您可以設定程式碼分析在每次建置專案時執行。 您也可以手動執行程式碼分析。  
  
 若要針對方案執行程式碼分析：  
  
- 在 [建置]**** 功能表上，選擇 [針對方案執行程式碼分析]****。  
  
  若要針對專案執行程式碼分析：  
  
- 在 [方案總管] 中，選擇專案的名稱。  
  
- 在 [**組建**] 功能表上，選擇 [針對*專案名稱***執行程式碼分析**]。  
  
  編譯專案或方案並執行程式碼分析。 結果隨即顯示在 [程式碼分析] 視窗中。  
  
## <a name="analyze-and-resolve-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> 分析和解決程式碼分析警告  
 若要分析特定警告，請在 [程式碼分析] 視窗中選擇警告的標題。 隨即展開警告以顯示問題的其他資訊。 如果可能的話，程式碼分析會顯示導致警告的行號和分析邏輯。 如需警告的詳細資訊，包括可能的問題方案，請選擇警告識別碼，顯示 MSND 文件庫中有關訊息的說明主題。  
  
 展開警告時，造成警告的程式碼行會在 Visual Studio 程式碼編輯器中反白顯示。  
  
 在您了解問題之後，就可以在程式碼中解決問題。 然後重新執行程式碼分析來確定 [程式碼分析] 視窗中不會再次出現警告，且您的修正尚未引發新的警告。  
  
> [!TIP]
> 您可以從 [程式碼分析] 視窗重新執行程式碼分析。 選擇 [ **分析** ] 按鈕，然後選擇分析的範圍。 您可以在整個方案或選取的專案上重新執行分析。  
  
## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> 隱藏程式碼分析警告  
 有時候您可能決定不修正程式碼分析警告。 您可能會判斷解決這項警告需要太多重新編碼，而在任何實際實作程式碼時會有問題發生的可能性。 或是，您可能會認為警告中使用的分析對於特定內容是不適當的。 您可以隱藏個別的警告，使之不再出現於 [程式碼分析] 視窗中。  
  
 隱藏警告：  
  
1. 如果未顯示詳細資訊，請選擇警告標題以展開它。  
  
2. 選擇警告下方的 [動作]**** 連結。  
  
3. 選擇 [ **隱藏訊息** ]，然後選擇 [ **來源**]。  
  
   隱藏訊息會插入 `#pragma warning (disable:` *warningid 因而* `)` ，以隱藏程式程式碼的警告。  
  
## <a name="creating-work-items-for-code-analysis-warnings"></a><a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> 建立程式碼分析警告的工作專案  
 若要記錄來自 Visual Studio 的錯誤，您可以使用工作項目追蹤功能。 若要使用這項功能，您必須連接到 Team Foundation Server 的執行個體。  
  
 **建立一或多個 C/C++ 程式碼警告的工作項目**  
  
1. 在 [程式碼分析] 視窗中，展開並選取警告  
  
2. 在警告的快捷方式功能表上，選擇 [ **建立工作專案**]，然後選擇 [工作專案類型]。  
  
3. Visual Studio 會建立選定警告的單一工作項目，並在 IDE 的文件視窗中顯示工作項目。  
  
4. 新增任何其他資訊，然後選擇 [ **儲存工作專案**]。  
  
## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> 搜尋和篩選程式代碼分析結果  
 您可以在多專案方案中搜尋警告訊息的詳細清單，以及篩選警告。  
  
1. **若要依標題或警告識別碼篩選警告**：在 [ **篩選** ] 文字方塊中輸入關鍵字。  
  
2. **若要依專案篩選警告**：在多專案方案中，選擇 [程式碼分析] 視窗右上方清單中的一或多個專案。 選擇要顯示所有警告的方案名稱。  
  
3. **依嚴重性篩選警告**：根據預設，系統會將 **警告**的嚴重性指派給程式碼分析訊息。 您可以將一或多個訊息的嚴重性指派為自訂規則集中的 **錯誤** 。 選擇 [ **警告** ] 或 [ **錯誤** ]，僅顯示指派給個別嚴重性的訊息。 選擇 [ **全部** ] 以顯示所有訊息。
