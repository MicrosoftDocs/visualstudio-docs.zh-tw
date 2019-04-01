---
title: 建立單元測試專案
ms.date: 01/29/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: ca83689628f02a8c7a2e0166b390d5b277086c1d
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416132"
---
# <a name="create-a-unit-test-project"></a>建立單元測試專案

單元測試通常會反映測試之程式碼的結構。 例如，單元測試專案會針對產品中的每個程式碼專案建立。 測試專案可位於與實際程式碼相同的方案中，或位於其他方案中。 您在方案中可以有多個單元測試專案。

> [!NOTE]
> 機器碼的單元測試位置和測試專案結構可能會與本文章中所描述的結構不同。 如需詳細資訊，請參閱[撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)。

## <a name="to-create-a-unit-test-project"></a>建立單元測試專案

1. 在 [檔案] 功能表上，選擇 [新增] > [專案] 或按 **Crtl**+**Shift**+**N**。

::: moniker range="vs-2017"

2. 在 [新增專案] 對話方塊中，展開 [已安裝] 節點，選擇您想要用於測試專案的語言，然後選擇 [測試]。

3. 若要使用其中一個 Microsoft 單元測試架構，請從專案範本清單中選擇 [單元測試專案]  。 否則，請選擇您所要使用單元測試架構的專案範本。 為專案命名，然後按一下 [確定]。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [建立新專案] 頁面的 [搜尋] 方塊中鍵入**單元測試**。 搜尋 [單元測試專案 (.NET Framework)] 專案範本，然後按一下 [下一步]。

3. 在 [設定新專案] 頁面上輸入您專案的名稱，然後按一下 [建立]。

::: moniker-end

4. 在單元測試專案中，加入受測程式碼的參考。 若要將參考新增至相同解決方案中的程式碼專案：

   1. 在 [方案總管] 中選取測試專案。

   2. 在 [專案]  功能表上，選擇 [加入參考] 。

   3. 在 [參考管理員] 中，選取 [專案] 底下的 [解決方案] 節點。 選取您想要測試的程式碼專案，然後選取 [確定]。

   如果您要測試的程式碼在另一個位置，請參閱[管理專案中的參考](../ide/managing-references-in-a-project.md)了解加入參考的相關資訊。

## <a name="next-steps"></a>後續步驟

查看下列其中一個小節：

**撰寫單元測試**

- [對程式碼進行單元測試](../test/unit-test-your-code.md)

- [撰寫 C/C++ 的單元測試](writing-unit-tests-for-c-cpp.md)

- [在單元測試中使用 MSTest 架構](using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests.md)

**執行單元測試**

- [使用測試總管執行單元測試](../test/run-unit-tests-with-test-explorer.md)