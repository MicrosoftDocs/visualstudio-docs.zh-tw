---
title: 分析器規則的嚴重性和隱藏項目
ms.date: 03/26/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, managed code
- analyzers
- Roslyn analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 56637ee7826b944d739e170faf22ae354abd8adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62821293"
---
# <a name="use-roslyn-analyzers"></a>使用 Roslyn 分析器

.NET 編譯器平台 ("Roslyn") 分析器規則，或*診斷*，當您輸入時，分析 C# 或 Visual Basic 程式碼。 每一個診斷已為您的專案將會覆寫預設嚴重性和隱藏狀態。 本文章涵蓋設定規則的重要性，使用規則集，並抑制違規。

## <a name="analyzers-in-solution-explorer"></a>在 [方案總管] 中的分析器

您可以執行大部分的自訂分析器診斷，從**方案總管 中**。 如果您[安裝分析器](../code-quality/install-roslyn-analyzers.md)成為 NuGet 套件**分析器**節點會顯示在**參考**或**相依性**中的節點**方案總管 中**。 如果您展開**分析器**，然後展開其中一個分析器組件，您會看到組件中的所有診斷。

![在方案總管 中的 分析器 節點](media/analyzers-expanded-in-solution-explorer.png)

您可以檢視診斷，包括其描述和預設嚴重性中的屬性**屬性**視窗。 若要檢視屬性，以滑鼠右鍵按一下規則，然後選取**屬性**，或是選取的規則，然後按**Alt**+**Enter**。

![在 [屬性] 視窗中的診斷屬性](media/analyzer-diagnostic-properties.png)

若要查看診斷的線上文件，以滑鼠右鍵按一下此診斷，並選取**檢視有助於**。

中的每個診斷旁的圖示**方案總管 中**對應至您在規則集編輯器中開啟時看到的圖示：

- "i"是圓形中的指出[嚴重性](#rule-severity)的**資訊**
- "！"中的三角形表示[嚴重性](#rule-severity)的**警告**
- 在圓形中的"x"表示[嚴重性](#rule-severity)的**錯誤**
- "i"是淺色背景圓圈會指示[嚴重性](#rule-severity)的**隱藏**
- 在圓形中的向下箭號表示會隱藏診斷

![在 [方案總管] 中的診斷圖示](media/diagnostics-icons-solution-explorer.png)

## <a name="rule-sets"></a>規則集

A[規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)是儲存個別的診斷的嚴重性和隱藏項目狀態的 XML 檔案。

> [!NOTE]
> 規則集可以包含靜態 （二進位） 的程式碼分析和 Roslyn 分析器的規則。

若要編輯的規則集編輯器中設定使用中的規則，以滑鼠右鍵按一下**參考** > **分析器**中的節點**方案總管] 中**，然後選取**開啟 [作用中的規則集**。 如果這是您正在編輯的規則集的第一次時，Visual Studio 會建立一份預設的規則集檔案，它*\<專案名稱 >.ruleset*，並將它加入至您的專案。 此自訂的規則集也會變成作用中的規則設定為您的專案。

若要變更專案中設定使用中的規則，瀏覽至**程式碼分析**專案屬性 索引標籤。 選取下方的清單設定的規則**執行此規則集**。 若要開啟規則集，請選取**開啟**。

> [!NOTE]
> .NET core 和.NET Standard 專案不會支援功能表命令的規則集所適用**方案總管**，例如**開啟作用中規則集**。 若要指定非預設規則集，是針對.NET Core 或.NET Standard 專案，以手動方式[新增**CodeAnalysisRuleSet**屬性設為專案檔案](using-rule-sets-to-group-code-analysis-rules.md#specify-a-rule-set-for-a-project)。 您可以設定 Visual Studio 中設定的規則，規則集編輯器 UI 內的規則。

## <a name="rule-severity"></a>規則嚴重性

您可以設定分析器規則的嚴重性或*診斷*，如果您[安裝分析器](../code-quality/install-roslyn-analyzers.md)NuGet 套件的形式。 下表顯示診斷的嚴重性選項：

|嚴重性|建置階段行為|編輯器的行為|
|-|-|-|
|錯誤|違規如下所示*錯誤*中**錯誤清單**命令列建置輸出，以及會導致組建失敗。|違規的程式碼會加上底線以紅色曲線，並以在捲軸的小型紅色方塊標示。|
|警告|違規如下所示*警告*中**錯誤清單**和在命令列建置輸出，但不是會造成建置失敗。|違規的程式碼會加上底線以綠色曲線，並標示在捲軸的小型綠色方塊。|
|資訊|違規如下所示*訊息*中**錯誤清單**，完全不會在命令列組建輸出。|違規的程式碼會加上底線以灰色曲線，並標示在捲軸的小型灰色方塊。|
|Hidden|非-使用者可以看見。|非-使用者可以看見。 診斷會回報給 IDE 診斷引擎，不過。|
|None|完全隱藏。|完全隱藏。|

此外，您可以 「 重設 」 規則的嚴重性設定為**預設**。 每一個診斷的中可以看到預設嚴重性**屬性**視窗。

下列螢幕擷取畫面會顯示三個不同的診斷違規，在程式碼編輯器中，三個不同的嚴重性。 請注意，曲線，以及在右側的捲軸的小型方塊的色彩。

![在程式碼編輯器的錯誤、 警告和資訊違規](media/diagnostics-severity-colors.png)

下列螢幕擷取畫面會顯示相同的三個違規濆婞剢謅**錯誤清單**:

![在 錯誤清單中的錯誤、 警告和資訊違規](media/diagnostics-severities-in-error-list.png)

您可以變更規則的嚴重性**方案總管**，或在 *\<projectname >.ruleset*變更中的規則的嚴重性之後加入至方案的檔案**方案總管 中**。

![在 [方案總管] 中的規則集檔案](media/ruleset-in-solution-explorer.png)

### <a name="set-rule-severity-from-solution-explorer"></a>從 [方案總管] 中的設定規則嚴重性

1. 在 **方案總管**，展開**參考** > **分析器**(**相依性** >  **分析器**.NET Core 專案)。

1. 展開包含您想要設定嚴重性以用於的規則的組件。

1. 以滑鼠右鍵按一下規則，然後選取**設定規則集合嚴重性**。 在飛出功能表中，選取 [嚴重性] 選項的其中一個。

   此規則的嚴重性會儲存在使用中的規則集檔案。

### <a name="set-rule-severity-in-the-rule-set-file"></a>在 規則集檔案中設定規則嚴重性

1. 開啟[規則集](analyzer-rule-sets.md)按兩下檔案**方案總管**，並選取**開啟作用中規則集**上按一下滑鼠右鍵功能表**分析器**節點，或選取**開放**上**程式碼分析**專案屬性頁。

1. 瀏覽至規則，藉由展開其包含的組件。

1. 在 **動作**欄中選取的值，以開啟下拉式清單中，然後從清單中選取想要的嚴重性。

   ![在編輯器中開啟的規則集檔案](media/ruleset-file-in-editor.png)

## <a name="suppress-violations"></a>隱藏違規

有多種方式可用來隱藏規則違規：

- 從**分析**功能表

   選取 **分析** > **執行程式碼分析和隱藏作用中問題**在功能表列上隱藏所有目前的違規情形。 這有時候稱為 「 基準 」。

- 從**方案總管**

   若要隱藏在違規**方案總管 中**，設定規則的嚴重性**無**。

- 從**規則集編輯器**

   若要隱藏的規則集編輯器的違規，取消選取其名稱旁邊的方塊，或設定**動作**要**無**。

- 從**程式碼編輯器**

   若要隱藏程式碼編輯器中的違規，將游標放在一行程式碼的違規和按下**Ctrl**+**。** 若要開啟 **快速動作**功能表。 選取 **隱藏 CAXXXX** > **來源中/隱藏項目檔**。

   ![隱藏診斷的快速動作 功能表](media/suppress-diagnostic-from-editor.png)

- 從**錯誤清單**

   您可以隱藏來自一或多個診斷**錯誤清單**藉由選取您想要隱藏的項目，然後用滑鼠右鍵按一下並選取**隱藏** > **中 Source/In隱藏項目檔**。

   - 如果要抑制**在原始程式檔**，則**預覽變更** 對話方塊隨即開啟並顯示預覽C# [#pragma 警告](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)或 Visual Basic [#Disable警告](/dotnet/visual-basic/language-reference/directives/directives)指示詞加入至原始程式碼。

      ![在程式碼檔案中加入 #pragma 警告的預覽](media/pragma-warning-preview.png)

   - 如果您選取**檔案中的隱藏項目**，則**預覽變更** 對話方塊隨即開啟並顯示預覽<xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>會新增至全域隱藏項目檔案的屬性。

      ![新增 SuppressMessage 屬性隱藏項目檔案的預覽](media/preview-changes-in-suppression-file.png)

   在 **預覽變更**對話方塊中，選取**套用**。

   > [!NOTE]
   > 如果您沒有看到**抑制**中的功能表選項**方案總管 中**，違規可能來自組建並不是即時的分析。 **錯誤清單**顯示診斷或規則違規，同時從即時程式碼分析，以及建置。 因為組建診斷可能會過期，比方說，如果您已編輯的程式碼來修正此違規情形，但尚未重建，您無法隱藏來自這些診斷**錯誤清單**。 來自即時分析或 IntelliSense、 診斷都一律是最新與目前的來源，並可從隱藏**錯誤清單**。 若要排除*建置*診斷從您的選取範圍中，切換**錯誤清單**來源篩選器，從**組建 + IntelliSense**至**只 Intellisense**. 然後，選取您想要隱藏並繼續如先前所述的診斷。
   >
   > ![在 Visual Studio 中的錯誤清單來源篩選器](media/error-list-filter.png)

## <a name="command-line-usage"></a>命令列使用方式

當您建置您的專案，在命令列時，組建輸出中會出現規則違規，如果符合下列條件：

- 分析器會安裝為 Nuget 套件，而不是 VSIX 擴充功能。

- 在專案的程式碼中違反一或多個規則。

- [嚴重性](#rule-severity)違反規則的設定為**警告**，在此情況下違規不會造成建置失敗，或**錯誤**，違反在此情況下會造成建置失敗。

是否會顯示規則的違規，就不會影響組建輸出的詳細資訊。 即使**安靜**詳細等級，出現在組建輸出的規則違規。

> [!TIP]
> 如果您已經習慣從命令列中，不論是透過執行靜態程式碼分析*FxCopCmd.exe*或透過與 msbuild **RunCodeAnalysis**旗標的以下是如何執行該作業使用 Roslyn 分析器。

若要查看在命令列分析器違規，當您建置使用 msbuild 的專案時，執行如下命令：

```cmd
msbuild myproject.csproj /target:rebuild /verbosity:minimal
```

下圖顯示建置專案，其中包含分析器規則的違規情況的命令列組建輸出：

![包含違規的 MSBuild 輸出](media/command-line-build-analyzers.png)

## <a name="dependent-projects"></a>相依的專案

在.NET Core 專案中，如果您加入至專案的 NuGet 分析器參考這些分析器會自動加入至相依專案太。 若要停用此行為，例如，如果相依的專案是單元測試專案，將標示為私用中的 NuGet 套件 *.csproj*或是 *.vbproj*檔案參考的專案，藉由設定**PrivateAssets**屬性：

```xml
<PackageReference Include="Microsoft.CodeAnalysis.FxCopAnalyzers" Version="2.9.0" PrivateAssets="all" />
```

## <a name="see-also"></a>另請參閱

- [在 Visual Studio 中的 Roslyn 分析器的概觀](../code-quality/roslyn-analyzers-overview.md)
- [送出的 Roslyn 分析器 bug](https://github.com/dotnet/roslyn-analyzers/issues)
- [使用規則集](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)
- [隱藏程式碼分析警告](../code-quality/in-source-suppression-overview.md)