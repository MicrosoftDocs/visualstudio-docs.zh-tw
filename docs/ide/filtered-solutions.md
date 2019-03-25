---
title: 載入專案的子集
ms.date: 12/04/2018
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 67ebbd94298c3325560b64945bed51c09db93833
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "57983880"
---
# <a name="filtered-solutions-in-visual-studio"></a>Visual Studio 中已篩選的方案

**Visual Studio 2019 的新功能**

大型開發團隊經常使用包含多個專案的單一大型方案來共同作業。 然而，個別開發人員通常只會負責這些專案中的一小部分。 為了改善開啟大型方案時的效能，Visual Studio 2019 引進「方案篩選」功能。 方案篩選可讓您開啟僅載入所選專案的方案。 在方案中載入專案的子集，可減少方案負載、組建和測試執行時間，並提供更聚焦的檢閱。

提供下列功能︰

- 不載入任何方案中的專案來開啟方案，讓您可以更快取得程式碼。 開啟方案之後，您可以選擇要載入哪些專案。

- 當您重新開啟方案時，Visual Studio 會記住您在先前的工作階段中載入了哪些專案，並僅載入這些專案。

- 您可以建立方案篩選檔案以儲存一或多個專案載入組態，或與團隊成員共用組態。

## <a name="open-a-filtered-solution"></a>開啟已篩選的方案

若要開啟僅載入一部分專案的方案，請遵循下列步驟：

1. 在功能表列上選擇 [檔案] > [開啟] > [專案/方案]。

2. 在 [開啟專案] 對話方塊中選取解決方案，然後選取 [不要載入專案]。

   ![已選取不載入專案的 Visual Studio 開啟專案對話方塊](media/filtered-solutions/do-not-load-projects.png)

3. 選擇 [開啟]。

   會開啟已卸載所有專案的方案。

4. 在 [方案總管] 中，選取您希望載入的專案 (按下 **Ctrl** 同時對多個專案按一下以將其選取)，然後以滑鼠右鍵按一下專案，並選擇 [重新載入專案]。

   ![在 Visual Studio [方案總管] 中重新載入多個專案](media/filtered-solutions/reload-project.png)

   下次您在本機中開啟方案時，Visual Studio 會記住載入過哪些專案。

## <a name="toggle-unloaded-project-visibility"></a>切換已卸載專案的可見性

使用 [方案總管] 中的下列選擇之一，可讓您選擇要查看方案中的所有專案，或僅查看已載入的專案：

- 以滑鼠右鍵按一下您的方案，並選取 [顯示已卸載專案] 或 [隱藏已卸載專案]。

- 選取 [顯示所有檔案] 按鈕來切換已卸載專案的可見性。

   ![Visual Studio [方案總管] 中的顯示所有檔案按鈕](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>方案篩選檔案

如果您希望共用您的專案載入組態，或將其認可至原始檔控制，您可以建立方案篩選器檔案 (其副檔名為 *.slnf*)。 當您開啟方案篩選檔案時，方案會以載入指定專案並隱藏所有已卸載專案的方式，在 Visual Studio 中開啟。 您可以[切換](#toggle-unloaded-project-visibility)以檢視已卸載專案。

[方案總管] 中方案旁邊圖示中額外的漏斗圖圖像，可用於在視覺上區別方案篩選檔案與一般方案檔案。 篩選名稱和已載入的專案數目也會顯示在方案名稱旁邊。

![在 Visual Studio [方案總管] 中開啟的方案篩選檔案](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> 如果在您建立方案篩選檔案後將新專案新增至原始方案，新專案會在 [方案總管] 中顯示為已卸載專案。

### <a name="create-a-solution-filter-file"></a>建立方案篩選檔案

1. 在 [方案總管] 中以滑鼠右鍵按一下方案，然後選取 [儲存為方案篩選]。

   ![Visual Studio [方案總管] 中的 [儲存為方案篩選檔案] 功能表](media/filtered-solutions/save-as-solution-filter.png)

2. 選擇方案篩選檔案的名稱和位置。

建立方案篩選檔案後，該檔案會新增至**最近使用的專案和方案**清單，以方便您存取：

![在 Visual Studio 中開啟最近使用的檔案](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>另請參閱

- [自訂 [方案總管] 中的檔案巢狀](file-nesting-solution-explorer.md)
- [最佳化 Visual Studio 效能](optimize-visual-studio-performance.md)
