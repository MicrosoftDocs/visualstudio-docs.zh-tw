---
title: 建構模型方案
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: fba020f27db73c5a96225c777f68e21db449b331
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831533"
---
# <a name="structure-your-modeling-solution"></a>建構模型方案

若要在開發專案中有效使用模型，小組成員必須能夠同時處理不同專案部分的模型。 本主題建議的配置，是將應用程式分割成不同部分，其對應到整個分層圖的圖層。

若要快速在專案或子專案上啟動，擁有遵循所選專案結構的專案範本，會很有用。 本主題描述如何建立及使用此種範本。

本主題假設您正在處理的專案，大到需要多個小組成員，而且可能有多個小組。 專案的程式碼和模型儲存在原始檔控制系統上，例如 [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]。 至少有部分小組成員使用 Visual Studio 開發模型，而其他小組成員可以使用其他 Visual Studio 版本檢視模型。

若要查看哪些版本的 Visual Studio 支援每個工具和模型化功能，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

## <a name="solution-structure"></a>方案結構

在中、大型專案中，小組的結構是以應用程式的結構為基礎。 每個小組都使用 Visual Studio 方案。

### <a name="to-divide-an-application-into-layers"></a>將應用程式分割到各圖層

1. 以應用程式結構為方案結構的基礎，例如 Web 應用程式、服務應用程式或桌面應用程式。 討論各種常見的架構[在 Microsoft 應用程式架構指南中的應用程式 Archetype](http://go.microsoft.com/fwlink/?LinkId=196681)。

2. 建立 Visual Studio 方案，我們稱之為架構方案。 這個方案會用以建立系統的整體設計。 它包含模型，但不含程式碼。

   加入此解決方案中的相依性圖表。 相依性在圖表上繪製您為您的應用程式所選擇的架構。 例如，圖表可能會顯示這些圖層與它們之間的相依性：簡報;商務邏輯;和資料。

4. 架構相依性圖表中建立個別的 Visual Studio 方案，每個圖層。

   這些方案會用以開發圖層的程式碼。

5. 建立代表一層及概念通用於所有圖層設計的模型。 排列模型，以便從架構方案查看所有模型，並從每個圖層查看相關的模型。

   下列兩個程序，任一皆可達成此目標。 第一種會為每個圖層建立個別的模型專案，第二種則會建立各圖層共用的單一模型專案。

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>每個圖層使用個別的模型專案

1. 在每個圖層方案中建立模型專案。

   此模型會包含描述的需求和設計，該圖層的圖表。 它也可以包含顯示巢狀圖層的相依性圖表。

   現在每個圖層都有一個模型，再加上一個應用程式架構模型。 每個模型都包含在自己的方案中。 這可讓小組成員同時在圖層上工作。

2. 請在架構方案中，加入每個圖層方案的模型專案。 若要執行此工作，請開啟架構方案。 在 **方案總管**，以滑鼠右鍵按一下方案節點、 指向 新增，然後按一下**現有專案**。 巡覽至某個圖層方案的模型專案 (.modelproj)。

   現在每個模型都會顯示在兩個方案中：其「主」方案和架構方案。

3. 每個圖層的模型專案，新增相依性圖表中。 開始使用的架構相依性圖表的複本。 您可以刪除不是相依性圖表的相依性的組件。

   您也可以新增相依性圖表，代表此圖層的詳細的結構。

   這些圖表是用於驗證在此圖層中開發的程式碼。

4. 在架構方案中，使用 Visual Studio 編輯所有圖層的需求和設計模型。

   在每個圖層方案中，開發該圖層的程式碼，參考模型。 如果您願意執行開發作業，但不使用同一部電腦更新模型，您可以使用無法建立模型的 Visual Studio 版本，讀取模型及開發程式碼。 您也可以從這些版本的模型產生程式碼。

   這個方法可確保同時編輯圖層模型的開發人員不會造成任何干擾。

   不過，因為模型是分開的，所以很難參考通用概念。 每個模型都必須有自己的項目複本，能夠從其他圖層與架構依存此項目複本。 相依性圖表中每個圖層必須保持與架構相依性圖表的同步處理。 當這些項目變更時，很難保持同步，雖然您可以開發工具來完成這項作業。

#### <a name="use-a-separate-package-for-each-layer"></a>每個圖層使用個別的套件

1. 在每個圖層的方案中，加入架構模型專案。 在**方案總管**，以滑鼠右鍵按一下方案節點，指向**新增**，然後按一下 **現有專案**。 現在從每個方案都可以存取單一模型專案：架構專案及每個圖層的開發專案。

2. 在共用模型，建立一個封裝每個圖層：在 [**方案總管] 中**，選取模型專案。 在  **UML 模型總管**，以滑鼠右鍵按一下模型根節點，指向**新增**，然後按一下 **封裝**。

   每個封裝將包含圖表，描述需求和對應圖層的設計。

3. 如有需要，加入本機的相依性圖表，每個圖層的內部結構。

   這個方法可讓每個圖層的設計項目直接參考圖層的設計項目，及其依存的通用架構。

   雖然在不同套件上同時執行工作可能會導致某些衝突，但也很容易管理，因為套件存放在不同的檔案中。

## <a name="create-architecture-templates"></a>建立架構範本

在實務上，您不在此同時，建立您所有的 Visual Studio 解決方案，但將它們加入隨著專案進展。 您可能會也使用相同的方案結構在未來的專案。 您可以建立方案或專案範本，以利快速建立新的方案。 您可以擷取 Visual Studio 整合擴充功能 (VSIX) 中的範本，讓它容易散發和安裝在其他電腦上。

例如，如果您經常使用有簡報、商務和資料圖層的解決方案，您可以設定範本，讓它建立的新方案都有這個結構。

### <a name="to-create-a-solution-template"></a>建立方案範本

1. [下載並安裝匯出範本精靈](http://go.microsoft.com/fwlink/?LinkId=196686)。

2. 建立要用做未來專案起點的方案結構。

3. 按一下 [檔案]  功能表上的 [匯出範本為 VSIX] 。

   **匯出範本為 VSIX 精靈**隨即開啟。

4. 遵循精靈中的指示，選取要包含在範本中的專案，提供範本的名稱和描述，並指定輸出位置。

## <a name="watch-a-video"></a>觀看影片

[組織及管理您的模型](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>另請參閱

- [在開發程序中使用模型](../modeling/use-models-in-your-development-process.md)
- [Visual Studio 架構工具指南](../modeling/visual-studio-architecture-tooling-guidance.md)
