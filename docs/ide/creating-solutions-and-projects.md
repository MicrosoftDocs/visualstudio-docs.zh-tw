---
title: 使用解決方案與專案
description: 瞭解方案和專案之間的差異，以及如何在 Visual Studio 中使用它們。
ms.custom: SEO-VS-2020, contperf-fy21q2
ms.date: 02/06/2018
ms.topic: how-to
f1_keywords:
- vs.openprojectfromweb
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6649b313d4ab03c1f096a6bcbc466cb338f427c
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684035"
---
# <a name="work-with-solutions-and-projects"></a>使用解決方案與專案

「專案」用以保存在 Visual Studio 中建置您應用程式所需的項目，例如原始程式碼檔、點陣圖、圖示，以及元件和服務參考。 當您建立新的專案時，Visual Studio 會建立一個包含該專案的「解決方案」。 接著可以視需要將新的或現有專案新增至解決方案。 解決方案也可以包含未連線至任何特定專案的檔案。

![方案/專案階層架構](./media/vside-proj-soln.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱[在 Visual Studio for Mac 中建立專案](/visualstudio/mac/create-new-projects)。

您可以在稱為 **方案總管** 的工具視窗中，檢視方案和專案。 下列螢幕擷取畫面顯示方案總管中的範例解決方案 (**BikeSharing.Xamarin-UWP**) 包含兩個專案：**BikeSharing.Clients.Core** 和 **BikeSharing.Clients.Windows**。 每個專案包含多個檔案、資料夾和參考。 以粗體顯示的專案名稱是「啟始專案」，也就是當您執行應用程式時所啟動的專案。 您可以指定哪一個專案是啟始專案。

![內含專案的方案總管](./media/vside-solution-explorer-projects.png)

雖然您可以將必要檔案新增至專案來自行建構專案，但 Visual Studio 也提供一系列專案範本，方便您著手進行。 從範本建立新的專案提供您一個專案，其中包含適用於該專案類型的基本資訊，而且您可以視需求重新命名檔案，或是將新的或現有程式碼和其他資源新增至專案。

也就是說，在 Visual Studio 中開發應用程式不需要方案和專案。 您也可以直接開啟從 Git 複製或從其他位置下載的程式碼。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="create-a-project-from-a-project-template"></a>從專案範本建立專案

如需從範本建立新專案的資訊，請參閱[在 Visual Studio 中建立新專案](create-new-project.md)。

## <a name="create-a-project-from-existing-code-files"></a>從現有程式碼檔案建立專案

如果您有程式碼來源檔案的集合，您可以輕鬆地將其新增至專案。

1. 在功能表上 **，選取 [**  >    >  **從現有程式碼** 檔案新增專案]。

1. 在 [ **從現有程式碼檔建立專案** ] 嚮導的 [ **您要建立哪一種類型的專案？** ] 下拉式清單方塊中，選取您要的專案類型，然後選取 [ **下一步]** 按鈕。

1. 在精靈中，瀏覽至檔案的位置，然後在 [名稱] 方塊中輸入新專案的名稱。 當您完成時，請選取 [ **完成]** 按鈕。

> [!NOTE]
> 這個選項最適合用於相對簡單的檔案集合。 目前僅支援 c + +、Apache Cordova、Visual Basic 和 c # 專案類型。

## <a name="add-files-to-a-solution"></a>將檔案新增至方案

如果您有一個套用至多個專案的檔案 (例如方案的讀我檔案)，或邏輯上位於方案層級而不是特定專案下的其他檔案，則可以將這些檔案新增至方案本身。 若要將專案加入至方案，請在內容 (以滑鼠右鍵按一下 **方案總管** 中方案節點的) 功能表，然後選取 [**加入**  >  **新專案**] 或 [**加入**  >  **現有專案**]。

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>建立以特定 .NET Framework 版本為目標的 .NET 專案

當您建立 .NET Framework 專案時，您可以指定要讓專案使用的特定 .NET Framework 版本。 (當您建立 .NET Core 專案時，您不會指定 Framework 版本。)

::: moniker range="vs-2017"

若要指定 .NET Framework 版本，請選取 [**新增專案**] 對話方塊中的 [**架構**] 下拉式功能表。

![[新增專案] 對話方塊中的 [Framework] 下拉式清單](./media/vside-newproject-framework.png)

> [!NOTE]
> 您必須在系統上安裝 .NET Framework 3.5，才能存取早於 .NET Framework 4 的 .NET Framework 版本。

::: moniker-end

::: moniker range=">=vs-2019"

若要指定 .NET Framework 版本，請選取 [**建立新專案**] 頁面上的 [**架構**] 下拉式功能表。

![[設定新專案] 中的 Framework 選取器](media/vs-2019/configure-new-project-framework.png)

::: moniker-end

## <a name="create-empty-solutions"></a>建立空的方案

您也可以建立不含專案的空方案。 這可能比較適合您想要從頭建構方案和專案的情況。

### <a name="to-create-an-empty-solution"></a>建立空的方案

1. 在功能表列上 **，選取 [** 檔案  >  **新增**  >  **專案**]。

::: moniker range="vs-2017"

2. 在左側 (**範本** ]) 窗格中，在展開的清單中選取 **其他專案類型** > **Visual Studio 方案** 。

3. 在中間窗格選取 [空白方案] 。

4. 輸入解決方案的 **名稱** 和 **位置** 值，然後選取 **[確定]**。

::: moniker-end

::: moniker range=">=vs-2019"

2. 在 [建立新專案] 頁面的 [搜尋] 方塊中鍵入 **解決方案**。

3. 選取 [空白方案] 範本，然後按一下 [下一步]。

4. 輸入方案的 **名稱** 和 **位置** 值，然後選取 [ **建立**]。

::: moniker-end

建立空的方案之後，您可以在 [專案] 功能表上，選擇 [新增項目] 或 [新增現有項目]，將新專案或項目或是現有專案或項目新增至該方案。

如前所述，您也可以開啟程式碼檔案而不需要專案或解決方案。 若要了解以此方式開發程式碼，請參閱[在 Visual Studio 中不使用專案或解決方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

::: moniker range="vs-2017"

## <a name="create-a-temporary-project"></a>建立暫存專案

(僅限 C# 和 Visual Basic)

如果您建立 .NET 專案而不指定磁碟位置，它會是暫存專案。 暫存專案可讓您試驗 .NET 專案。 使用暫存專案時，隨時都可以選擇儲存或捨棄它。

若要建立暫存專案，請先移至 [**工具**  >  **選項**  >  **專案和方案**  >  **一般**]，並取消核取 [**建立新專案時，儲存新專案**] 核取方塊。 然後像往常一樣開啟 [新增專案] 對話方塊。

::: moniker-end

## <a name="delete-a-solution-project-or-item"></a>刪除方案、專案或項目

您可以永久刪除方案及其內容，但不使用 Visual Studio IDE。 刪除 Visual Studio 中的項目只會將這些項目從目前的方案或專案移除。 若要從系統永久刪除解決方案或其他元件，請使用檔案總管來刪除包含 .sln 和 .suo 解決方案檔案的資料夾。 不過，在永久刪除方案之前，建議您備份任何專案或檔案，以免再次需要。

> [!NOTE]
> .suo 檔案是隱藏檔案，不會顯示在預設檔案總管設定下。 若要顯示隱藏的檔案，請在檔案總管的 [檢視] 功能表中，選取 [隱藏的項目] 核取方塊。

### <a name="permanently-delete-a-solution"></a>永久刪除解決方案

1. 在 **方案總管** 中，在您要刪除之方案的快顯功能表 (內容功能表) 上，選取 [ **開啟資料夾] 檔案總管**。

1. 在 [檔案總管] 中，瀏覽上一層。

1. 選取包含解決方案的資料夾，然後按下 **Delete** 鍵。

## <a name="see-also"></a>另請參閱

- [方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [GitHub 上的 Microsoft 開放原始碼存放庫](https://github.com/Microsoft)
- [開發人員程式碼範例](https://code.msdn.microsoft.com/)
- [建立專案 (Visual Studio for Mac)](/visualstudio/mac/create-new-projects)
