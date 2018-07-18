---
title: 使用，並在 Visual Studio 中設定 Roslyn 分析器
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2e99a98f5ea4cca5891d416bdc13656b3173a40f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31925116"
---
# <a name="configure-and-use-roslyn-analyzer-rules"></a>設定及使用 Roslyn 分析器規則

.NET 編譯器平台 ("Roslyn") 分析程式的規則，或*診斷*，當您輸入時，分析 C# 或 Visual Basic 程式碼。 每個診斷具有可以覆寫專案的預設嚴重性和隱藏項目狀態。 本文涵蓋設定規則的重要性，使用規則集，並抑制違規。

## <a name="analyzers-in-solution-explorer"></a>在 [方案總管] 的分析器

您可以執行大部分的分析器診斷資訊收集從自訂**方案總管 中**。 如果您[安裝分析器](../code-quality/install-roslyn-analyzers.md)以 NuGet 套件，**分析器**節點會出現在**參考**或**相依性**中的節點**方案總管 中**。 如果您展開**分析器**，然後展開其中一個分析器組件，您會看到組件中的所有診斷。

![在 [方案總管] 的分析器節點](media/analyzers-expanded-in-solution-explorer.png)

您可以檢視的診斷，包括其描述和預設嚴重性中屬性**屬性**視窗。 若要檢視屬性，以滑鼠右鍵按一下規則，然後選取**屬性**，或是選取的規則，然後按**Alt**+**Enter**。

![在 [屬性] 視窗中的診斷屬性](media/analyzer-diagnostic-properties.png)

若要查看診斷的線上文件，以滑鼠右鍵按一下此診斷，並選取**檢視說明**。

中的每個診斷旁邊的圖示**方案總管 中**對應至您在規則集編輯器中開啟時看到的圖示：

- "i"是圓形中有指出[嚴重性](#rule-severity)的**資訊**
- "！"中的三角形表示[嚴重性](#rule-severity)的**警告**
- "x"是圓形中有指出[嚴重性](#rule-severity)的**錯誤**
- 淺色背景的圓形中有"i"表示[嚴重性](#rule-severity)的**隱藏**
- 向下的箭號是圓形中有指出診斷已隱藏

![在 [方案總管] 中的診斷圖示](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>規則集

A[規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)是 XML 檔案，儲存的嚴重性和隱藏狀態，以個別的診斷資訊。 規則集套用至單一專案，而且專案可以有多個規則集。 若要檢視作用中規則集編輯器中，以滑鼠右鍵按一下**分析器**節點**方案總管 中**選取**開啟作用中規則集**。 如果這是您要存取規則的第一次設定，為名為的檔案 *\<projectname >.ruleset*加入至專案，而且會出現在**方案總管 中**。

> [!NOTE]
> 規則集包括靜態 （二進位） 的程式碼分析和 Roslyn analyzer 規則。

您可以變更作用中的專案上設定的規則**程式碼分析**的專案屬性 索引標籤。 選取規則集**執行此規則集**下拉式清單。 您也可以開啟規則集從**程式碼分析**屬性頁面中的選取**開啟**。

## <a name="rule-severity"></a>規則的嚴重性

您可以設定分析器規則的嚴重性或*診斷*，如果您[安裝分析器](../code-quality/install-roslyn-analyzers.md)以 NuGet 套件。 下表顯示診斷的嚴重性選項：

|嚴重性|在建置階段行為|編輯器的行為|
|-|-|-|
|錯誤|違規會顯示為*錯誤*中**錯誤清單**命令列組建輸出，以及會導致組建失敗。|違規的程式碼是以紅色波浪形底線，而且標示為小型的紅色方塊，捲軸中加上底線。|
|警告|違規會顯示為*警告*中**錯誤清單**及命令列組建輸出，但是不會導致組建失敗。|違規的程式碼是具有綠色曲線，而且標示為小型的綠色方塊，捲軸中加上底線。|
|資訊|違規會顯示為*訊息*中**錯誤清單**，完全不會在命令列組建輸出。|違規的程式碼會以灰色曲線，而且標示為小型的灰色方塊，捲軸中加上底線。|
|Hidden|非-使用者可以看見。|非-使用者可以看見。 診斷會回報給 IDE 診斷引擎，不過。|
|無|完全隱藏。|完全隱藏。|

此外，您可以 「 重設 」 規則的嚴重性設定為**預設**。 每一個診斷的中，可以看到預設嚴重性**屬性**視窗。

下列螢幕擷取畫面會顯示三個不同的診斷違規，在程式碼編輯器中，有三種不同的嚴重性。 請注意，曲線，以及小方塊右側的捲軸中的色彩。

![程式碼編輯器中的錯誤、 警告和資訊違規](media/diagnostics-severity-colors.png)

下列螢幕擷取畫面會顯示相同的三個違規濆婞剢謅**錯誤清單**:

![錯誤清單中的錯誤、 警告和資訊違規](media/diagnostics-severities-in-error-list.png)

您可以變更規則的嚴重性**方案總管 中**，或在 *\<projectname >.ruleset*變更中的規則的嚴重性之後加入至方案的檔案**方案總管 中**。

![在 [方案總管] 中的規則集檔案](media/ruleset-in-solution-explorer.png)

### <a name="to-set-rule-severity-from-solution-explorer"></a>若要從方案總管 中設定規則的嚴重性

1. 在**方案總管 中**，依序展開**參考** > **分析器**(**相依性** >  **分析器**.NET Core 專案)。

1. 展開包含您想要設定嚴重性之的規則的組件。

1. 以滑鼠右鍵按一下規則，然後選取**設定規則設定嚴重性**。 在快顯功能表中，選取其中一個嚴重性選項。

   此規則的嚴重性會儲存在作用中規則集檔案。

### <a name="to-set-rule-severity-in-the-rule-set-file"></a>若要設定規則在規則中的嚴重性設定檔案

1. 開啟規則集檔案按兩下**方案總管 中**、 選取**開啟作用中規則集**的右鍵功能表**分析器** 節點，或選取**開啟**上**程式碼分析**專案屬性頁。

1. 瀏覽至規則擴充其包含的組件。

1. 在**動作**資料行中，選取要開啟下拉式清單中，值，並從清單中選取想要的嚴重性。

   ![在編輯器中開啟的規則集檔案](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>隱藏違規

有多種方式來隱藏規則違規：

- 若要抑制所有目前的違規，請選取**分析** > **執行程式碼分析並隱藏作用中問題**功能表列上。 這有時候稱為 「 基準 」。

- 若要隱藏從診斷**方案總管 中**，設定其嚴重性為**無**。

- 若要隱藏的規則集編輯器診斷，取消選取其名稱旁邊的方塊，或設定**動作**至**無**。

- 若要隱藏診斷，以從程式碼編輯器，將游標置於違規與按下的程式碼行**Ctrl**+**。** 若要開啟**快速控制項目**功能表。 選取**隱藏 CAxxxx** > **來源中**或**隱藏 CAxxxx** > **中隱藏項目檔**。

   ![隱藏診斷的快速動作 功能表](media/suppress-diagnostic-from-editor.png)

- 若要隱藏從診斷**錯誤清單**，以滑鼠右鍵按一下錯誤、 警告或訊息，並選取**抑制** > **在原始程式檔**或**隱藏** > **中隱藏項目檔**。

   - 如果您選取**在原始程式檔**、**預覽變更** 對話方塊隨即開啟並顯示 C# 的預覽[#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)或 Visual Basic [#Disable 警告](/dotnet/visual-basic/language-reference/directives/directives)指示詞加入至原始程式碼。

      ![程式碼檔案中加入 #pragma 警告預覽](media/pragma-warning-preview.png)

   - 如果您選取**中隱藏項目檔**、**預覽變更** 對話方塊隨即開啟並顯示預覽<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>會新增至全域隱藏項目檔案的屬性。

      ![SuppressMessage 屬性加入隱藏項目檔中的預覽](media/preview-changes-in-suppression-file.png)

   在**預覽變更**對話方塊中，選取**套用**。

> [!NOTE]
> 在.NET Core 專案中，如果您加入至 NuGet 分析器的專案參考這些分析器會自動加入至相依專案太。 若要停用此行為，例如，如果相依專案是單元測試專案，將標示為私用中的 NuGet 套件 *.csproj*或 *.vbproj*參考專案檔：
>
> ```xml
> <PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.6.0" PrivateAssets="all" />
> ```

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
- [送出 Roslyn 分析器 bug](https://github.com/dotnet/roslyn-analyzers/issues)
- [使用規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [隱藏程式碼分析警告](../code-quality/in-source-suppression-overview.md)