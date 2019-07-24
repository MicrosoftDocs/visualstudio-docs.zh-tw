---
title: 使用相依性圖表驗證程式碼
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, validating
- validation, dependency diagrams
- validation, code
- code exploration, validating
- architecture, validating
- Visual Studio Ultimate, validating code
- validation, architecture
- validation, dependencies
- MSBuild, tasks
- MSBuild, dependency diagrams
- MSBuild, validating code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9786c35b81ac0ff4fd29ffe121aab7e1aa04f2f
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416442"
---
# <a name="validate-code-with-dependency-diagrams"></a>使用相依性圖表驗證程式碼

## <a name="why-use-dependency-diagrams"></a>為何要使用相依性圖表？

為確保程式碼不會與設計衝突, 請在 Visual Studio 中使用相依性圖表驗證程式代碼。 這可協助您：

- 尋找您程式碼中的相依性與相依性圖表相依性之間的衝突。

- 尋找可能會受到建議變更所影響的相依性。

   例如, 您可以編輯相依性圖表以顯示潛在的架構變更, 然後驗證程式代碼以查看受影響的相依性。

- 將程式碼重構或移轉至不同設計。

   在您將程式碼移至不同的架構時，請尋找需要運作的程式碼或相依性。

**需求**

- Visual Studio

  若要建立 .NET Core 專案的相依性圖表, 您必須具有 Visual Studio 2019 16.2 版或更新版本。

- 具有具有相依性圖表之模型專案的方案。 此相依性圖表必須連結至您要C#驗證之專案中的成品或 Visual Basic。 請參閱[從您的程式碼建立](../modeling/create-layer-diagrams-from-your-code.md)相依性圖表。

若要查看哪些版本的 Visual Studio 支援這項功能, 請參閱[架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

您可以在 Visual Studio 中或從命令提示字元, 手動從開啟的相依性圖表驗證程式代碼。 您也可以在執行本機組建或 Azure Pipelines 組建時, 自動驗證程式代碼。 請[參閱 Channel 9 影片:使用相依性圖表](http://go.microsoft.com/fwlink/?LinkID=252073)設計和驗證您的架構。

> [!IMPORTANT]
> 如果您想要使用 Team Foundation Server (TFS) 來執行圖層驗證, 您也必須在組建伺服器上安裝相同版本的 Visual Studio。

## <a name="live-dependency-validation"></a>即時相依性驗證

相依性驗證會即時進行, 而錯誤會立即顯示在**錯誤清單**中。

* C#和 Visual Basic 都支援即時驗證。

* 若要在使用即時相依性驗證時啟用完整的解決方案分析, 請從出現在**錯誤清單**中的 [金色] 列開啟 [選項] 設定。

  - 如果您不想要查看解決方案中的所有架構問題, 可以永久關閉金色列。
  - 如果您未啟用完整的解決方案分析, 則只會針對正在編輯的檔案進行分析。

* 升級專案以啟用即時驗證時, 會有一個對話方塊顯示轉換的進度。

* 更新專案以進行即時相依性驗證時, NuGet 套件的版本會針對所有專案升級為相同, 而且是使用中的最高版本。

* 加入新的相依性驗證專案會觸發專案更新。

## <a name="see-if-an-item-supports-validation"></a>查看項目是否支援驗證

您可以將圖層連結到網站、Office 檔、純文字檔, 以及跨多個應用程式共用之專案中的檔案, 但驗證程式不會包含這些檔案。 對於連結至個別圖層之專案或組件的參考，如果這些圖層之間沒有任何相依性，則不會出現驗證錯誤。 除非程式碼使用這些參考，否則不會考量此類參考的相依性。

1. 在相依性圖表上, 選取一或多個圖層, 以滑鼠右鍵按一下您的選取專案, 然後按一下 [ **View Links**]。

2. 在 [**圖層瀏覽器**] 中, 查看 [**支援驗證**] 資料行。 如果值為 false，則這個項目不支援驗證。

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>包含其他 .NET 組件和專案來進行驗證

當您將專案拖曳至相依性圖表時, 對應的 .NET 元件或專案的參考會自動加入至模型專案的 [**圖層參考**] 資料夾。 這個資料夾包含組件的參考以及驗證期間分析的專案。 您可以包含其他 .NET 元件和專案進行驗證, 而不需要手動將它們拖曳至相依性圖表。

1. 在**方案總管**中, 以滑鼠右鍵按一下模型專案或 [**圖層參考**] 資料夾, 然後按一下 [**加入參考**]。

2. 在 [**加入參考**] 對話方塊中, 選取元件或專案, 然後按一下 **[確定]** 。

## <a name="validate-code-manually"></a>手動驗證程式碼

如果您有連結至方案專案的開啟相依性圖表, 您可以從圖表執行 [**驗證**] 快捷方式命令。 您也可以使用命令提示字元執行**msbuild**命令, 並將 **/p: ValidateArchitecture**自訂屬性設定為**True**。 例如，在您變更程式碼時定期執行圖層驗證，以便早期攔截相依性衝突。

### <a name="validate-code-from-an-open-dependency-diagram"></a>從開啟的相依性圖表驗證程式代碼

1. 以滑鼠右鍵按一下圖表介面, 然後按一下 [**驗證架構**]。

    > [!NOTE]
    > 根據預設, 相依性圖表 (. .layerdiagram) 檔案上的 [**組建動作**] 屬性會設定為 [**驗證**], 讓圖表包含在驗證程式中。

     [**錯誤清單**] 視窗會報告任何發生的錯誤。 如需驗證錯誤的詳細資訊, 請參閱針對[圖層驗證問題進行疑難排解](#troubleshoot-layer-validation-issues)。

2. 若要查看每個錯誤的來源, 請按兩下 [**錯誤清單**] 視窗中的錯誤。

    > [!NOTE]
    > Visual Studio 可能會顯示 Code Map, 而不是錯誤的來源。 當程式碼與相依性圖表未指定的元件有相依性, 或此程式碼遺漏相依性圖表所指定的相依性時, 就會發生這種情況。 請檢閱 Code Map 或程式碼，以判斷相依性是否應存在。 如需 code map 的詳細資訊, 請參閱[對應方案之間](../modeling/map-dependencies-across-your-solutions.md)的相依性。

3. 若要管理錯誤, 請參閱[解決圖層驗證錯誤](#resolve-layer-validation-errors)。

### <a name="validate-code-at-the-command-prompt"></a>在命令提示字元驗證程式代碼

1. 開啟 Visual Studio 命令提示字元。

2. 選擇下列其中一項：

   - 若要根據方案中的特定模型專案來驗證程式代碼, 請使用下列自訂屬性執行 MSBuild。

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - 或 -

       流覽至包含模型專案 (. .modelproj) 檔案和相依性圖表的資料夾, 然後使用下列自訂屬性執行 MSBuild:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - 若要根據方案中的所有模型專案來驗證程式代碼, 請使用下列自訂屬性執行 MSBuild:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - 或 -

       流覽至 [方案] 資料夾, 其中必須包含包含相依性圖表的模型專案, 然後使用下列自訂屬性執行 MSBuild:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     發生的任何錯誤都將列出。 如需 MSBuild 的詳細資訊, 請參閱[msbuild](../msbuild/msbuild.md)和[msbuild](../msbuild/msbuild-task.md)工作。

   如需驗證錯誤的詳細資訊, 請參閱針對[圖層驗證問題進行疑難排解](#troubleshoot-layer-validation-issues)。

### <a name="manage-validation-errors"></a>管理驗證錯誤

在開發過程中，您可以隱藏驗證期間已報告過的某些衝突。 例如，您可能會想要隱藏已經處理的錯誤，或是與特定情節無關的錯誤。 當您隱藏錯誤時, 在 Team Foundation 中記錄工作專案是個不錯的作法。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

#### <a name="create-a-work-item-for-a-validation-error"></a>建立驗證錯誤的工作專案

- 在 [**錯誤清單**] 視窗中, 以滑鼠右鍵按一下錯誤, 指向 [**建立工作專案**], 然後按一下您想要建立的工作專案類型。

使用下列工作來管理 [**錯誤清單**] 視窗中的驗證錯誤:

|**若要**|**請遵循下列步驟**|
|-|-|
|在驗證期間隱藏選取的錯誤|以滑鼠右鍵按一下一個或多個選取的錯誤、指向 [**管理驗證錯誤**], 然後按一下 [**隱藏錯誤**]。<br /><br /> 隱藏的錯誤會以刪除線的格式出現。 當您下一次執行驗證時，這些錯誤將不會出現。<br /><br /> 隱藏的錯誤會在對應的相依性圖表檔案的隱藏檔案中追蹤。|
|停止隱藏選取的錯誤|以滑鼠右鍵按一下選取的隱藏錯誤或錯誤, 指向 [**管理驗證錯誤**], 然後按一下 [**停止隱藏錯誤**]。<br /><br /> 選取的隱藏錯誤將會在下一次執行驗證時出現。|
|還原 [**錯誤清單**] 視窗中所有隱藏的錯誤|以滑鼠右鍵按一下 [**錯誤清單**] 視窗中的任何位置, 指向 [**管理驗證錯誤**], 然後按一下 [**顯示所有隱藏的錯誤**]。|
|從 [**錯誤清單**] 視窗中隱藏所有隱藏的錯誤|以滑鼠右鍵按一下 [**錯誤清單**] 視窗中的任何位置, 指向 [**管理驗證錯誤**], 然後按一下 [**隱藏所有隱藏的錯誤**]。|

## <a name="validate-code-automatically"></a>自動驗證程式碼

您可以在每次執行本機組建時執行圖層驗證。 如果您的小組使用 Azure DevOps, 您可以使用閘道簽入來執行圖層驗證, 您可以藉由建立自訂 MSBuild 工作來指定, 以及使用組建報告收集驗證錯誤。 若要建立閘道簽入組建, 請參閱[TFVC 閘道簽入](/azure/devops/pipelines/build/triggers#gated)。

### <a name="to-validate-code-automatically-during-a-local-build"></a>在本機組建執行期間自動驗證程式碼

使用文字編輯器來開啟模型專案 (.modelproj) 檔案，然後加入下列屬性：

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\-或-

1. 在**方案總管**中, 以滑鼠右鍵按一下包含相依性圖表或圖表的模型專案, 然後按一下 [**屬性**]。

2. 在 [**屬性**] 視窗中, 將模型專案的 [**驗證架構**] 屬性設定為 [ **True**]。

    這會將模型專案納入驗證程序中。

3. 在**方案總管**中, 按一下您要用於驗證的相依性圖表 (. .layerdiagram) 檔案。

4. 在 [**屬性**] 視窗中, 確認圖表的 [**組建動作**] 屬性已設定為 [**驗證**]。

    這包括驗證程式中的相依性圖表。

若要在錯誤清單視窗中管理錯誤, 請參閱[解決層驗證錯誤](#resolve-layer-validation-errors)。

## <a name="troubleshoot-layer-validation-issues"></a>疑難排解圖層驗證問題

下列表格描述圖層驗證的問題及其解決方式。 這些問題不同於因程式碼與設計衝突而導致的錯誤。 如需有關這些錯誤的詳細資訊, 請參閱針對[圖層驗證問題進行疑難排解](#troubleshoot-layer-validation-issues)。

|**問題**|**可能的原因**|**解決方法**|
|-|-|-|
|發生非預期的驗證錯誤。|在方案總管中的其他相依性圖表中, 或位於相同模型專案中的相依性圖表, 驗證無法運作。 以這種方式複製的相依性圖表包含與原始相依性圖表相同的參考。|將新的相依性圖表加入至模型專案。<br /><br /> 將元素從來源相依性圖表複製到新的圖表。|

## <a name="resolve-layer-validation-errors"></a>解決圖層驗證錯誤

當您針對相依性圖表驗證程式代碼時, 當程式碼與設計衝突時, 就會發生驗證錯誤。 例如，下列條件可能造成圖層驗證發生錯誤：

- 成品指派給錯誤的圖層。 在此情況下，請移動成品。

- 類別之類的成品以與架構發生衝突的方式使用另一個類別。 在此情況下，請重構程式碼以移除相依性。

若要解決這些錯誤，請更新程式碼直到驗證時不再出現錯誤為止。 您可以透過互動方式執行這項工作。

以下章節說明用於這些錯誤的語法，解釋這些錯誤的意義，並且建議解析或管理這些錯誤的作法。

|**語法**|**描述**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*是與相依性圖表上的圖層相關聯的成品。<br /><br /> *ArtifactTypeN*是*ArtifactN*的類型, 例如**類別**或**方法**, 例如:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|命名空間的名稱。|
|*LayerNameN*|相依性圖表上的圖層名稱。|
|*DependencyType*|*Artifact1*與*Artifact2*之間的相依性關聯性類型。 例如, *Artifact1*具有與*Artifact2*的**呼叫**關聯性。|

| **錯誤語法** | **錯誤描述** |
|-|-|
| DV0001:**相關性無效** | 當對應至圖層的程式碼專案 (命名空間、類型、成員) 參考對應至另一個圖層的程式碼專案, 但在包含此圖層的相依性驗證圖表中, 這些圖層之間沒有相依性箭號時, 就會回報此問題。 這是相依性條件約束違規。 |
| DV1001:**不正確命名空間名稱** | 此問題會在與圖層相關聯的程式碼元素上回報, 「允許的命名空間名稱」屬性不包含定義此程式碼專案的命名空間。 這是命名條件約束違規。 請注意, 「允許的命名空間名稱」的語法是命名空間的分號清單, 其中的程式碼專案會被允許定義。 |
| DV1002:**Unreferenceable 命名空間的相依性** | 此問題會在與圖層相關聯的程式碼元素上回報, 並參考在該圖層的 "Unreferenceable Namespace" 屬性中定義的命名空間中所定義的另一個程式碼專案。 這是命名條件約束違規。 請注意, "Unreferenceable 命名空間" 屬性定義為以分號分隔的命名空間清單, 不應在與此圖層相關聯的程式碼元素中參考。 |
| DV1003:**不允許的命名空間名稱** | 此問題會在與圖層相關聯的程式碼元素上回報, 而「不允許的命名空間名稱」屬性包含定義此程式碼專案的命名空間。 這是命名條件約束違規。 請注意, 「不允許的命名空間名稱」屬性會定義為以分號分隔的命名空間清單, 其中不應定義與此圖層相關聯的程式碼元素。 |
| DV3001:**遺失連結** | 圖層 '*LayerName*' 連結至 ' 成品 ', 但找不到該*專案*。 您是否遺漏了組件參考? |
| DV9001:**架構分析發現內部錯誤** | 結果可能不完整。 如需詳細資訊，請參閱詳細建置事件記錄檔或輸出視窗。 |

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的即時相依性驗證](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)
- [影片：即時驗證架構相依性](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
