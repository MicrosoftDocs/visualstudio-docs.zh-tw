---
title: 管理 Python 應用程式專案
description: Visual Studio 中的專案會管理檔案之間的相依性，以及應用程式中的關聯性複雜度。
ms.date: 03/18/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 09203557fd9adcd6580dfafa981d6ed4f80eca16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936453"
---
# <a name="python-projects-in-visual-studio"></a>Visual Studio 中的 Python 專案

定義 Python 應用程式時，通常僅使用資料夾和檔案，但隨著應用程式變得越來越大，此結構會變得相當複雜，且可能牽涉到自動產生的檔案、Web 應用程式的 JavaScript 等。 Visual Studio 專案有利於管理此複雜部分。 專案 (*.pyproj* 檔案) 會識別與您專案建立關聯的所有來源和內容檔案、包含每個檔案的組建資訊、維護要與來源控制系統整合的資訊，以及協助您將應用程式整理成邏輯元件。

![[方案總管] 中的 Python 專案](media/projects-solution-explorer.png)

此外，您一律是在 Visual Studio 的「方案」內管理專案，方案中可以包含任意數目、可能彼此參考的專案。 例如，Python 專案可以參考實作延伸模組的 C++ 專案。 透過此關聯性，當您開始對 Python 專案進行偵錯時，Visual Studio 就會自動建置 C++ 專案 (如有必要)。 (如需一般的討論，請參閱 [Visual Studio 中的方案和專案](../ide/solutions-and-projects-in-visual-studio.md))。

Visual Studio 提供各種 Python 專案範本，可讓您快速設定一些應用程式結構，包括可從現有資料夾樹狀目錄建立專案的範本，以及可建立乾淨空專案的範本。 如需相關索引，請參閱[專案範本](#project-templates)。

<a name="lightweight-usage-project-free"></a>

::: moniker range=">=vs-2019"
> [!Tip]
> Visual Studio 2019 支援開啟包含 Python 程式碼的資料夾，並執行該程式碼，不需要建立 Visual Studio 專案和方案檔案。 如需詳細資訊，請參閱 [快速入門：在資料夾中開啟及執行 Python 程式碼](quickstart-05-python-visual-studio-open-folder.md)。 但是使用專案檔有一些優點，如本節所述。
::: moniker-end

> [!Tip]
> 即使沒有專案，所有的 Visual Studio 版本也都能搭配 Python 程式碼順利運作。 例如，您可以單獨開啟 Python 檔案來使用自動完成、IntelliSense 及偵錯功能 (透過在編輯器中按一下滑鼠右鍵，然後選取 [啟動並偵錯])。 不過，因為這類程式碼一律會使用預設全域環境，所以如果程式碼是針對不同的環境，則您可能就會看到不正確的完成或錯誤。 此外，Visual Studio 還會分析您從中開啟單一檔案之資料夾中的所有檔案和套件，這可能會耗費相當多的 CPU 時間。
>
> 如[從現有的檔案建立專案](#create-project-from-existing-files)中所述，從現有的程式碼建立 Visual Studio 專案相當簡單。

![影片深入探討的影片攝影機圖示](../install/media/video-icon.png "觀看影片") [：搭配 Python 專案使用原始檔控制](https://youtu.be/Aq8eqApnugM) (youtube.com、>8m 分55秒) 。

## <a name="add-files-assign-a-startup-file-and-set-environments"></a>新增檔案、指派啟動檔案及設定環境

當您開發應用程式時，通常需要將不同類型的新檔案新增至專案中。 藉由在專案上按一下滑鼠右鍵，然後選取 [**加入**  >  您要用來流覽檔案的 **現有專案**] 或 [**加入** 新專案]，即可新增這類檔案，其中會顯示  >  具有各種專案範本的對話方塊。 如[項目範本](python-item-templates.md)參考上所述，選項包含空白 Python 檔案、Python 類別、單元測試，以及各種與 Web 應用程式相關的檔案。 您可以使用測試專案來探索這些選項，以了解您的 Visual Studio 版本中提供了哪些選項。

每個 Python 專案都有一個指派的啟動檔案，在 [方案總管] 中是以粗體顯示。 啟動檔案是當您啟動偵錯工具時所執行的檔案 (**F5** 或 **Debug**  >  **開始調試** 程式) 或當您在 **互動式** 視窗中執行專案時 (以 Python 互動) 來 **切換** + **Alt** + **F5** 或 **Debug**  >  **Execute 專案**。 若要變更它，以滑鼠右鍵按一下新檔案，然後選取 [設定為啟動項目] (或者，在較舊的 Visual Studio 版本中選取 [設定為啟動檔案])。

> [!Tip]
> 如果您從專案中移除選取的啟動檔案，且未選取新的啟動檔案，則在您嘗試執行該專案時，Visual Studio 就無法知道要啟動哪一個 Python 檔案。 在此情況下，Visual Studio 2017 15.6 版及更新版本會顯示錯誤；較舊的版本則會在 Python 解譯器執行的情況下開啟輸出視窗，或是您會看見該輸出視窗出現並立即消失。 如果您遇到這些行為，請確認您已指派啟動檔案。
>
> 若您因任何原因要讓輸出視窗保持開啟，請以滑鼠右鍵按一下專案，選取 [屬性]，選取 [偵錯] 索引標籤，然後將 `-i` 加入 [解譯器引數] 欄位。 此引數會導致解譯器在程式完成之後進入互動模式，藉此讓視窗保持開啟，直到您輸入 **Ctrl** + **Z**  >  **enter** 結束為止。

::: moniker range="vs-2017"
新專案一律會與預設的全域 Python 環境關聯。 若要將專案與不同的環境 (包括虛擬環境) 建立關聯，請在專案中的 [Python 環境] 節點上按一下滑鼠右鍵，選取 [新增/移除 Python 環境]，然後選取您想要的環境。
::: moniker-end
::: moniker range=">=vs-2019"
新專案一律會與預設的全域 Python 環境關聯。 若要將專案與不同的環境 (包括虛擬環境) 建立關聯，在專案中的 [Python 環境] 節點上按一下滑鼠右鍵、選取 [新增環境...]，然後選取所需的環境。 您也可以使用工具列上的 [環境] 下拉式控制項，或在專案中新增另一個。

![Python 工具列上的 [新增環境] 命令](media/environments/environments-toolbar-2019.png)
::: moniker-end

若要變更使用中環境，在 [方案總管] 中以滑鼠右鍵按一下所需的環境，然後選取 [啟用環境]，如下所示。 如需詳細資訊，請參閱[選取專案的環境](selecting-a-python-environment-for-a-project.md)。

![啟用 Python 專案的環境](media/projects-activate-environment.png)

<a name="project-types"></a>

## <a name="project-templates"></a>專案範本

Visual Studio 提供您一些方法來建立 Python 專案，不論是從頭開始或是從現有的程式碼，都可以。 若要使用範本，請選取 **[檔案**  >  **新增**  >  **專案**] 功能表命令，或以滑鼠右鍵按一下 **方案總管** 中的方案，然後選取 [**加入**  >  **新** 專案]，這兩個專案都會顯示下方的 [**新增專案**] 對話方塊。 若要查看 Python 特定的範本，請搜尋 "Python" 或選取 **已安裝** 的  >  **python** 節點：

![含有 Python 範本的 [新增專案] 對話方塊](media/projects-new-project-dialog.png)

下表摘要說明 Visual Studio 2017 和更新版本中可用的範本 (並非所有範本在所有舊版中都有提供)：

| 範本 | 描述 |
| --- | --- |
| [**從現有 Python 程式碼**](#create-project-from-existing-files) | 從資料夾結構中的現有 Python 程式碼建立 Visual Studio 專案。  |
| **Python 應用程式** | 具有單一空白原始程式檔的新 Python 應用程式基本專案結構。 根據預設，專案會在預設全域環境的主控台解譯器中執行，您可以透過[指派不同的環境](selecting-a-python-environment-for-a-project.md)來變更此環境。 |
| [**Azure 雲端服務**](python-azure-cloud-service-project-template.md) | 以 Python 撰寫的 Azure 雲端服務專案。 |
| [**Web 專案**](python-web-application-project-templates.md) | 針對以各種不同的架構 (包括 Bottle、Django 和 Flask) 為基礎的 Web 應用程式專案。 |
| **IronPython 應用程式** | 與「Python 應用程式」範本類似，但預設使用 IronPython，可藉由 .NET 語言啟用 .NET 互通性及混合模式偵錯。 |
| **IronPython WPF 應用程式** | 一種針對應用程式的使用者介面使用 IronPython 搭配 Windows Presentation Foundation XAML 檔案的專案結構。 Visual Studio 會提供 XAML UI 設計工具、程式碼後置可以用 Python 來撰寫，應用程式則會在不顯示主控台的情況下執行。 |
| **IronPython Silverlight 網頁** | 一種使用 Silverlight 在瀏覽器中執行的 IronPython 專案。 應用程式的 Python 程式碼會以指令碼的形式包含在網頁中。 重複使用指令碼標記會向下拖曳出一些 JavaScript 程式碼，這些程式碼會將在 Silverlight 內部執行的 IronPython 初始化，而您的 Python 程式碼便可從中與 DOM 互動。 |
| **IronPython Windows Forms 應用程式** | 一種使用 IronPython 的專案結構，其中是使用程式碼搭配 Windows Forms 來建立 UI。 應用程式會在不顯示主控台的情況下執行。 |
| **背景應用程式 (IoT)** | 支援將 Python 專案部署成在裝置上以背景服務的形式執行。 如需詳細資訊，請瀏覽 [Windows IoT 開發人員中心](https://dev.windows.com/en-us/iot)。 |
| **Python 延伸模組** | 如果您已在 Visual Studio 2017 或更新版本中安裝 **Python 原生開發工具** 與 Python 工作負載 (請參閱 [安裝](installing-python-support-in-visual-studio.md))，此範本會出現在 Visual C++ 下。 它提供的 C++ 延伸模組 DLL 的核心結構，類似於[建立適用於 Python 的 C++ 延伸模組](working-with-c-cpp-python-in-visual-studio.md)中所述。 |

> [!Note]
> 因為 Python 是解譯式語言，所以 Visual Studio 中的 Python 專案不會產生其他編譯式語言專案 (例如 C#) 所產生的獨立式可執行檔。 如需詳細資訊，請參閱[問與答](overview-of-python-tools-for-visual-studio.md#questions-and-answers)。

<a name="create-project-from-existing-files"></a>

### <a name="create-a-project-from-existing-files"></a>從現有的檔案建立專案

> [!Important]
> 此處所述的程序不會移動或複製原始程式檔。 如果您想要使用複本，請先複製資料夾。

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>連結的檔案

連結的檔案就是已導入專案中但通常位於應用程式專案資料夾外的檔案。 它們在 [方案總管] 中會顯示為帶有重疊捷徑圖示的一般檔案：![連結的檔案圖示](media/projects-linked-file-icon.png)

連結的檔案是在 *.pyproj* 檔案中使用 `<Compile Include="...">` 元素來指定的。 如果連結的檔案使用目錄結構以外的相對路徑，或者如果它們使用 **方案總管** 內的路徑，則是明確的：

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

在下列任一情況下，會忽略連結的檔案：

- 連結的檔案包含 Link 中繼資料，且 Include 屬性中指定的路徑是在專案目錄內
- 連結的檔案與專案階層中已存在的檔案重複
- 連結的檔案包含 Link 中繼資料，且 Link 路徑是位於專案階層外的相對路徑
- 連結路徑是根目錄

### <a name="work-with-linked-files"></a>使用連結的檔案

若要加入現有的專案作為連結，請以滑鼠右鍵按一下專案中要加入檔案的資料夾，然後選取 [**加入**  >  **現有專案**]。 在顯示的對話方塊中，選取檔案，然後從 [新增] 按鈕上的下拉式清單中選擇 [新增作為連結]。 在沒有任何衝突檔案的情況下，此命令會在選取的資料夾中建立連結。 不過，如果已經有相同名稱的檔案存在，或專案中已經有該檔案的連結存在，就不會新增連結。

如果您嘗試連結到已經存在於專案資料夾中的檔案，則系統會將它新增為一般檔案，而不是連結。 若要將檔案轉換成連結，請 **選取**  >  [檔案 **另存** 新檔]，將檔案儲存到專案階層外的位置;Visual Studio 會自動將它轉換成連結。 同樣地，您 **可以使用 [** 檔案另存新檔]，將檔案  >  儲存在專案階層內的某個位置，以轉換回連結。

如果您在 [方案總管] 中移動某個連結的檔案，則會移動該連結，但實際的檔案不受影響。 同樣地，刪除某個連結將會移除該連結，但不會影響檔案。

您無法重新命名連結的檔案。

## <a name="references"></a>參考資料

Visual Studio 專案支援新增對專案和延伸模組的參考，這些參考會顯示在 [方案總管] 中的 [參考] 節點底下：

![Python 專案中的擴充功能參考](media/projects-extension-references.png)

擴充功能參考通常會指出專案之間的相依性，並可用來在設計階段提供 IntelliSense 或在編譯階段提供連結。 Python 專案使用參考的方式類似，但由於 Python 的動態本質緣故，因此主要是在設計階段使用參考來提供改進的 IntelliSense。 您也可以使用它們來部署到 Microsoft Azure 以安裝額外的相依性。

### <a name="extension-modules"></a>延伸模組

對 *.pyd* 檔案的參考可以為產生的模組啟用 IntelliSense。 Visual Studio 會將 *.pyd* 檔案載入到 Python 解譯器，並自我檢查其類型和函式。 它也會嘗試剖析文件字串來找出提供簽章說明的函式。

在任何時候，只要更新磁碟上的延伸模組，Visual Studio 就會在背景中重新分析該模組。 這個動作不會影響執行時間行為，但在分析完成之前，無法使用某些完成。

您可能也需要新增包含該模組之資料夾的[搜尋路徑](search-paths.md)。

### <a name="net-projects"></a>.NET 專案

使用 IronPython 時，您可以新增對 .NET 組件的參考來啟用 IntelliSense。 針對您方案中的 .NET 專案，請在 Python 專案中的 [參考] 節點上按一下滑鼠右鍵，依序選取 [加入參考]、[專案] 索引標籤，然後瀏覽至想要的專案。 針對您已個別下載的 DLL，請改為選取 [瀏覽] 索引標籤，然後瀏覽至想要的 DLL。

由於 IronPython 的參考必須等到呼叫 `clr.AddReference('<AssemblyName>')` 之後才可供使用，因此您還必須將適當的 `clr.AddReference` 呼叫加入到組件中，通常是在程式碼的開頭處。 例如，**IronPython Windows Forms 應用程式** 專案範本在 Visual Studio 中建立的程式碼在檔案頂端包含兩個呼叫：

```python
import clr
clr.AddReference('System.Drawing')
clr.AddReference('System.Windows.Forms')

from System.Drawing import *
from System.Windows.Forms import *

# Other code omitted
```

### <a name="webpi-projects"></a>WebPI 專案

您可以新增對 WebPI 產品項目的參考以供部署到 Microsoft Azure 雲端服務，然後在該處透過 WebPI 摘要來安裝額外的元件。 根據預設，顯示的摘要為 Python 特定，並且包含 Django、CPython 及其他核心元件。 您也可以選取自己的摘要，如以下所示。 當發佈到 Microsoft Azure 時，安裝作業將會安裝所有參考的產品。

> [!IMPORTANT]
> 在 Visual Studio 2017 或 Visual Studio 2019 中無法使用 WebPI 專案。

![WebPI 參考](media/projects-webPI-components.png)
