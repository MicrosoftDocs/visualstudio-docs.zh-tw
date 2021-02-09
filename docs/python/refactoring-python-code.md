---
title: 重構 Python 程式碼
description: Visual Studio 可藉由重新命名識別碼、擷取方法、新增匯入及移除未使用的匯入，輕鬆地重構 Python 程式碼。
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8eb46f324359549d7f74e8edd90d3056820e234e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902379"
---
# <a name="refactor-python-code"></a>重構 Python 程式碼

Visual Studio 提供數個可自動轉換和清除 Python 原始程式碼的命令︰

- [重新命名](#rename)會重新命名選取的類別、方法或變數名稱
- [擷取方法](#extract-method)會從選取的程式碼建立新方法
- [加入匯入](#add-import)提供智慧標籤以加入遺漏的匯入
- [移除未使用的匯入](#remove-unused-imports)會移除未使用的匯入

## <a name="rename"></a>重新命名

1. 以滑鼠右鍵按一下您要重新命名的識別項並選取 [重新命名]，或將插入點放在該識別項中並選取 [編輯] > [重構] > [重新命名] 功能表命令 (**F2**)。
2. 在出現的 [重新命名] 對話方塊中，輸入識別項的新名稱並選取 [確定]：

   ![[重新命名] 的新識別項名稱提示](media/code-refactor-rename-1.png)

3. 在下一個對話方塊中，選取您的程式碼中要套用重新命名的檔案和執行個體；選取任一個別的執行個體以預覽特定變更︰

   ![選取套用變更的位置的 [重新命名 (Rename)] 對話方塊](media/code-refactor-rename-2.png)

4. 選取 [套用] 以變更您的原始程式碼檔。 (這個動作無法回復。)

## <a name="extract-method"></a>擷取方法

1. 選取要擷取到另一個方法的程式碼或運算式。
2. 選取 [**編輯**  >  **重構**  >  **解壓縮方法**] 功能表命令或輸入 **Ctrl** + **R**  >  **M**。
3. 在出現的對話方塊中，輸入新的方法名稱，指定將它擷取到何處，並選取所有結束變數。 未選取要結束的變數會轉變成方法引數︰

   ![[擷取方法] 對話方塊](media/code-refactor-extract-method-1.png)

4. 選取 [確定]，就會依此修改程式碼︰

   ![擷取方法的結果](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>加入匯入

當您將插入點放在缺少類型資訊的識別項時，Visual Studio 會提供智慧標籤 (程式碼左邊的燈泡圖示)，其命令會新增必要的 `import` 或 `from ... import` 陳述式︰

![加入匯入的智慧標籤](media/code-refactor-add-import-1.png)

Visual Studio 為最上層的套件和目前專案和標準程式庫中的模組，提供 `import` 完成。 Visual Studio 也為子模組和子套件，以及模組成員提供 `from ... import` 完成。 完成包括函式、類別或匯出的資料。 選取任一個選項會將陳述式加入其他匯入後的檔案頂端，或加入現有的 `from ... import` 陳述式 (如果相同的模組已經匯入)。

![加入匯入的結果](media/code-refactor-add-import-2.png)

Visual Studio 會嘗試篩選出未實際定義於模組中的成員，例如已匯入另一個模組，但不是執行匯入之模組子系的模組。 比方說，許多模組使用 `import sys` 而非 `from xyz import sys`，因此即使模組遺漏的 `__all__` 成員不含 `sys`，也不會完成匯入其他模組的 `sys`。

同樣地，Visual Studio 會篩選從其他模組或內建命名空間匯入的函式。 例如，如果模組從 `sys` 模組匯入 `settrace` 函式，則理論上您可以從該模組將它匯入。 但最好直接使用 `import settrace from sys`，Visual Studio 才會具體提供該陳述式。

最後，如果某項目正常情況下會被排除，但卻具有其他會包含的值 (例如，因為已在模組中指派名稱的值)，Visual Studio 仍會排除匯入。 此行為假設不應該匯出值，因為它定義在另一個模組中，因此其他的指派可能是空的值，也不會匯出。

## <a name="remove-unused-imports"></a>移除未使用的匯入

撰寫程式碼時，對於完全未使用的模組，很容易得到 `import` 陳述式。 由於 Visual Studio 會分析您的程式碼，因此可以查看範圍內是否使用了匯入的名稱 (陳述式即出現在該範圍下方)，以自動判斷 `import` 陳述式是否有必要。

使用滑鼠右鍵按一下編輯器中的任何位置，然後選取 [ **移除匯入**]，這可讓您從 **所有範圍** 或只移除 **目前的範圍** 中移除選項：

![[移除匯入] 功能表](media/code-refactor-remove-imports-1.png)

Visual Studio 即會對程式碼進行適當的變更：

![移除匯入的結果](media/code-refactor-remove-imports-2.png)

請注意，Visual Studio 不考慮控制流程；如果您在 `import` 陳述式之前使用名稱，即視同實際使用該名稱。 Visual Studio 也會忽略所有 `from __future__` 匯入、在類別定義內執行的匯入，以及來自 `from ... import *` 陳述式的匯入。
