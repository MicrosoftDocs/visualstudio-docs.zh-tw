---
title: 在 Visual Studio 中建立方案和專案
ms.date: 02/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ee3a25927b80db9da2c9217ce04cf2064e26461a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34571610"
---
# <a name="create-solutions-and-projects"></a>建立方案和專案

「專案」是 Visual Studio 中的邏輯容器，用以保存建置您應用程式所需的項目，例如原始程式碼檔、點陣圖、圖示，以及元件和服務參考。 當您建立新的專案時，Visual Studio 會建立一個包含該專案的「解決方案」。 接著可以視需要將新的或現有專案新增至解決方案。 解決方案也可以包含未連線至任何特定專案的檔案。

![方案/專案階層架構](./media/vside-proj-soln.png)

您可以在稱為**方案總管**的工具視窗中，檢視方案和專案。 下列螢幕擷取畫面顯示方案總管中的範例解決方案 (**BikeSharing.Xamarin-UWP**) 包含兩個專案：**BikeSharing.Clients.Core** 和 **BikeSharing.Clients.Windows**。 每個專案包含多個檔案、資料夾和參考。 以粗體顯示的專案名稱是「啟始專案」，也就是當您執行應用程式時所啟動的專案。 您可以指定哪一個專案是啟始專案。

![內含專案的方案總管](./media/vside-solution-explorer-projects.png)

雖然您可以將必要檔案新增至專案來自行建構專案，但 Visual Studio 也提供一系列專案範本，方便您著手進行。 從範本建立新的專案提供您一個專案，其中包含適用於該專案類型的基本資訊，而且您可以視需求重新命名檔案，或是將新的或現有程式碼和其他資源新增至專案。

也就是說，在 Visual Studio 中開發應用程式不需要方案和專案。 您也可以直接開啟從 Git 複製或從其他位置下載的程式碼。 如需詳細資訊，請參閱[在 Visual Studio 中不使用專案或方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

> [!NOTE]
> 本主題中的描述以 Visual Studio Community 版本為基礎。 您看到的對話方塊與功能表命令，可能會依您的設定與 Visual Studio 版本而與此處描述的有所不同。 若要變更您的設定 (例如變更為 [一般] 或 [Visual C++] 設定)，請選擇 [工具]、[匯入和匯出設定]，然後選擇 [重設所有設定]。

## <a name="to-create-a-project-from-a-project-template"></a>從專案範本建立專案

1. 在 Visual Studio 中建立新的專案有多種方式。 在 [起始頁] 上，於 [搜尋專案範本] 方塊中輸入專案範本的名稱，或選擇 [建立新專案] 連結以開啟 [新增專案] 對話方塊。 您也可以選擇功能表列上的 [檔案] > [新增] > [專案]，或選擇工具列上的 [新增專案] 按鈕。

  ![起始頁](./media/vside-newproject1.png)

  在 [新增專案] 對話方塊中，可用的專案範本會出現在清單中的 [範本] 類別下。 範本會依程式設計語言和專案類型組織，例如 Visual C#、JavaScript 和 Azure Data Lake。

  ![[新增專案] 對話方塊](./media/vside-newproject-templates-list.png)

  > [!NOTE]
  > 所顯示的可用語言和專案範本清單取決於您執行的 Visual Studio 版本及安裝的工作負載。 若要了解如何安裝額外的工作負載，請參閱[透過新增或移除工作負載和元件來修改 Visual Studio 2017](../install/modify-visual-studio.md)。

1. 顯示您要使用之程式設計語言的範本清單，方法是選擇語言名稱旁的三角形，然後選擇專案類型。

  下列範例示範適用於 Visual C# .NET Core 專案的專案範本。

  ![專案範本](./media/new-project-dialog-net-core.png)

1. 在 [名稱] 方塊中輸入新專案的名稱。 您可以選擇將專案儲存在系統上的預設位置，或選擇 [瀏覽] 按鈕以尋找其他位置。

  您也可以選擇性地選擇變更方案名稱，或選擇 [新增至原始檔控制] 以將新專案新增至 Git 存放庫。

1. 選擇 [確定] 按鈕以建立方案和專案。

1. 如果您想要將其他專案新增至解決方案，請在方案總管中選擇方案節點，然後在功能表列上選擇 [專案] > [新增項目]。

## <a name="create-a-project-from-existing-code-files"></a>從現有程式碼檔案建立專案

如果您有程式碼來源檔案的集合，您可以輕鬆地將其新增至專案。

1. 在功能表上，選擇 [檔案] > [新增] > [現有程式碼中的專案]。

1. 在 [從現有程式碼檔建立專案精靈] 的 [您要建立的專案類型為何?] 下拉式清單方塊中，選擇您想要的專案類型，然後選擇 [下一步] 按鈕。

1. 在精靈中，瀏覽至檔案的位置，然後在 [名稱] 方塊中輸入新專案的名稱。 當您完成時，選擇 [完成] 按鈕。

> [!NOTE]
> 這個選項最適合用於相對簡單的檔案集合。 目前，只支援 Visual C++、Apache Cordova、Visual Basic 和 C# 專案類型。

## <a name="add-files-to-a-solution"></a>將檔案新增至方案

如果您有一個套用至多個專案的檔案 (例如方案的讀我檔案)，或邏輯上位於方案層級而不是特定專案下的其他檔案，則可以將這些檔案新增至方案本身。 若要將項目新增至方案，請在 [方案總管] 中方案節點的操作 (滑鼠右鍵) 功能表上，選擇 [新增] > [新增項目] 或 [新增] > [現有的項目]。

## <a name="create-a-net-project-that-targets-a-specific-version-of-the-net-framework"></a>建立以特定 .NET Framework 版本為目標的 .NET 專案

當您建立專案時，您可以指定專案所要使用的特定 .NET Framework 版本。 若要指定 .NET Framework 版本，請選擇 [新增專案] 對話方塊中的 [Framework] 下拉式功能表。

![[新增專案] 對話方塊中的 [Framework] 下拉式清單](./media/vside-newproject-framework.png)

> [!NOTE]
> 您必須在系統上安裝 .NET Framework 3.5，才能存取早於 .NET Framework 4 的 .NET Framework 版本。

## <a name="create-empty-solutions"></a>建立空的方案

您也可以建立不含專案的空方案。 這可能比較適合您想要從頭建構方案和專案的情況。

### <a name="to-create-an-empty-solution"></a>建立空的方案

1. 在功能表上，選擇 [檔案] > [新增] > [專案...]。

1. 在左側 ([範本]) 窗格中，在展開的清單中選擇 [其他專案類型] > [Visual Studio 方案]。

1. 在中間窗格選擇 [空白方案]。

1. 為您的方案輸入 [名稱] 和 [位置] 值，然後選擇 [確定]。

建立空的方案之後，您可以在 [專案] 功能表上，選擇 [新增項目] 或 [新增現有項目]，將新專案或項目或是現有專案或項目新增至該方案。

如前所述，您也可以開啟程式碼檔案而不需要專案或解決方案。 若要了解以此方式開發程式碼，請參閱[在 Visual Studio 中不使用專案或解決方案來開發程式碼](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)。

## <a name="create-a-temporary-project-c-and-visual-basic"></a>建立暫存的專案 (C# 和 Visual Basic)

如果您建立 .NET 專案而不指定磁碟位置，它會是暫存專案。 暫存專案可讓您試驗 .NET 專案。 使用暫存專案時，隨時都可以選擇儲存或捨棄它。

若要建立暫存專案，請先移至 [工具] > [選項] > [專案和方案] > [一般]，並取消選取 [建立時儲存新專案] 核取方塊。 然後像往常一樣開啟 [新增專案] 對話方塊。

## <a name="delete-a-solution-project-or-item"></a>刪除方案、專案或項目

您可以永久刪除方案及其內容，但不使用 Visual Studio IDE。 刪除 Visual Studio 中的項目只會將這些項目從目前的方案或專案移除。 若要從系統永久刪除解決方案或其他元件，請使用檔案總管來刪除包含 .sln 和 .suo 解決方案檔案的資料夾。 不過，在永久刪除方案之前，建議您備份任何專案或檔案，以免再次需要。

> [!NOTE]
> .suo 檔案是隱藏檔案，不會顯示在預設檔案總管設定下。 若要顯示隱藏的檔案，請在檔案總管的 [檢視] 功能表中，選取 [隱藏的項目] 核取方塊。

### <a name="to-permanently-delete-a-solution"></a>永久刪除方案

1. 在**方案總管**中，於您要刪除之方案的操作功能表上，選擇 [在檔案總管中開啟資料夾]。

1. 在 [檔案總管] 中，瀏覽上一層。

1. 選擇包含解決方案的資料夾，然後選擇 **DELETE** 鍵。

## <a name="see-also"></a>另請參閱

- [方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [GitHub 上的 Microsoft 開放原始碼存放庫](https://github.com/Microsoft)
- [開發人員程式碼範例](https://code.msdn.microsoft.com/)