---
title: MSBuild 中的方案篩選
description: 說明解決方案篩選器，並示範如何使用 MSBuild 建立方案篩選檔案。
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 998103828d20827e8a1d99e0cc34d7f9beb6bd7c
ms.sourcegitcommit: 9179c33a78c2ac690ce908d7c73eef50b6e367f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87401024"
---
# <a name="solution-filters-in-msbuild"></a>MSBuild 中的方案篩選

方案篩選檔案是副檔名為 *.slnf*的 JSON 檔案，指出要從方案中的所有專案建立或載入哪些專案。 從 MSBuild 16.7 開始，您可以在方案篩選檔案上叫用 MSBuild，以在啟用篩選的情況下建立解決方案。 

> [!NOTE]
> 方案篩選檔案可減少將載入或建立的專案集合，並簡化格式。 方案檔仍然是必要的。

## <a name="build-a-solution-filter-from-the-command-line"></a>從命令列建立解決方案篩選器

從命令列建立方案篩選檔案，會使用與建立方案檔完全相同的語法。 指定解決方案篩選器檔案，而不是要在啟用篩選的情況下建立的解決方案，如下所示：

```console
msbuild [options] solutionFilterFile.slnf
```

您也可以像平常一樣附加參數和額外的屬性。 請參閱[MSBuild 命令列參考](msbuild-command-line-reference.md)。 此命令會建立已篩選的專案及其相依的任何專案。 從命令列建立方案篩選器時，MSBuild 會自動遵循相依性。 如果專案是在篩選準則中指定，或由建立的專案所參考，它就會建立專案。

## <a name="solution-filter-files"></a>方案篩選檔案

您可以使用 Visual Studio 來處理方案篩選檔案。 在 Visual Studio 中開啟方案篩選器會顯示卸載的專案以及載入的專案，並讓您選擇載入更多專案來選取它們以進行建立。 您也可以載入初始專案相依于組建的所有專案，但這並非必要。 請參閱已[篩選的解決方案](../ide/filtered-solutions.md)。

方案篩選不一定要與方案位於相同的資料夾中。 方案檔的路徑會相對於方案篩選檔案的位置，但每個專案的路徑會相對於方案檔本身，而且應符合方案檔中的專案路徑。 下列範例示範相對路徑的用法：

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

路徑中的反斜線必須是兩個，因為它們是轉義的。

## <a name="example"></a>範例

以下是 Visual Studio 中篩選解決方案的範例：

![Visual Studio 中篩選解決方案的螢幕擷取畫面](media/solution-with-filter.png)

在此解決方案中，ProjectA 和 ProjectB 都會使用 ClassLibrary1，因此 ClassLibrary1 會列為專案參考。

以下是 Visual Studio 產生的解決方案篩選檔案：

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

在此範例中，當您使用已啟用篩選（使用命令）建立時 `MSBuild [options] MyFilter.slnf` ，MSBuild 會建立 MyApplication 和 ProjectA，因為它們會明確列在方案篩選檔案中。 在建立 ProjectA 時，MSBuild 會建立 ClassLibrary1，因為 ProjectA 會相依于此元件。  未建立 ProjectB。 （本討論會假設有一個全新的組建。 如果先前已建立專案，則一般規則適用于略過最新的專案。）

## <a name="see-also"></a>另請參閱

- [已篩選的解決方案](../ide/filtered-solutions.md)
- [MSBuild 命令列參考](msbuild-command-line-reference.md)
