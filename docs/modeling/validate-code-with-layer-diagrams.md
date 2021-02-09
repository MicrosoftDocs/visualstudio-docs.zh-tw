---
title: 使用相依性圖表驗證程式碼
description: 瞭解為了確保程式碼不會與設計產生衝突，您應該使用 Visual Studio 中的相依性圖表來驗證您的程式碼。
ms.custom: SEO-VS-2020
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e330b95d2de6da53d9d1bd0f3d553ab8319bdd04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924325"
---
# <a name="validate-code-with-dependency-diagrams"></a>使用相依性圖表驗證程式碼

## <a name="why-use-dependency-diagrams"></a>為何要使用相依性圖表？

若要確定程式碼不會與設計產生衝突，請使用 Visual Studio 中的相依性圖表來驗證您的程式碼。 這可協助您：

- 找出程式碼中的相依性與相依性圖表的相依性之間的衝突。

- 尋找可能會受到建議變更所影響的相依性。

   例如，您可以編輯相依性圖表以顯示可能的架構變更，然後驗證程式代碼以查看受影響的相依性。

- 將程式碼重構或移轉至不同設計。

   在您將程式碼移至不同的架構時，請尋找需要運作的程式碼或相依性。

**需求**

- Visual Studio

  若要建立 .NET Core 專案的相依性圖表，您必須有 Visual Studio 2019 16.2 版或更新版本。

- 具有具有相依性圖表之模型專案的方案。 此相依性圖表必須連結到您想要驗證的 c # 或 Visual Basic 專案中的構件。 請參閱 [從您的程式碼建立](../modeling/create-layer-diagrams-from-your-code.md)相依性圖表。

若要查看 Visual Studio 支援這項功能的版本，請參閱 [架構和模型工具的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

您可以在 Visual Studio 中或從命令提示字元，以手動方式從開啟的相依性圖表驗證程式代碼。 您也可以在執行本機組建或 Azure Pipelines 組建時，自動驗證程式代碼。 請參閱 [Channel 9 影片：使用相依性圖表設計及驗證您的架構](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)。

> [!IMPORTANT]
> 如果您想要使用 Team Foundation Server (TFS) 來執行圖層驗證，您也必須在組建伺服器上安裝相同版本的 Visual Studio。

## <a name="live-dependency-validation"></a>即時相依性驗證

相依性驗證會即時發生，錯誤會立即顯示在 [ **錯誤清單**] 中。

* C # 和 Visual Basic 支援即時驗證。

* 若要在使用即時相依性驗證時啟用完整的解決方案分析，請從 **錯誤清單** 中顯示的金色列開啟選項設定。

  - 如果您不想查看解決方案中的所有架構問題，您可以永久關閉金級列。
  - 如果您未啟用完整的解決方案分析，則只會針對正在編輯的檔案進行分析。

* 升級專案以啟用即時驗證時，對話方塊會顯示轉換的進度。

* 更新專案以進行即時相依性驗證時，會針對所有專案將 NuGet 套件的版本升級為相同，而且是使用中的最高版本。

* 加入新的相依性驗證專案會觸發專案更新。

## <a name="see-if-an-item-supports-validation"></a>查看項目是否支援驗證

您可以將圖層連結到網站、Office 檔、純文字檔案，以及跨多個應用程式共用之專案中的檔案，但驗證程式不會包含這些專案。 對於連結至個別圖層之專案或組件的參考，如果這些圖層之間沒有任何相依性，則不會出現驗證錯誤。 除非程式碼使用這些參考，否則不會考量此類參考的相依性。

1. 在相依性圖表上，選取一或多個圖層，以滑鼠右鍵按一下您的選取專案，然後按一下 [ **View Links**]。

2. 在 [ **圖層瀏覽器**] 中，查看 [ **支援驗證** ] 資料行。 如果值為 false，則這個項目不支援驗證。

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>包含其他 .NET 組件和專案來進行驗證

當您將專案拖曳至相依性圖表時，對應的 .NET 元件或專案的參考會自動加入至模型專案的 [ **圖層參考** ] 資料夾中。 這個資料夾包含組件的參考以及驗證期間分析的專案。 您可以包含其他 .NET 元件和專案以進行驗證，而不需要手動將它們拖曳至相依性圖表。

1. 在 **方案總管** 中，以滑鼠右鍵按一下模型專案或 [ **圖層參考** ] 資料夾，然後按一下 [ **加入參考**]。

2. 在 [ **加入參考** ] 對話方塊中，選取元件或專案，然後按一下 **[確定]**。

## <a name="validate-code-manually"></a>手動驗證程式碼

如果您有連結至方案專案的開啟相依性圖表，您可以從圖表執行 [ **驗證** 快速鍵] 命令。 您也可以使用命令提示字元執行 **msbuild** 命令，並將 **/p： ValidateArchitecture** 自訂屬性設定為 **True**。 例如，在您變更程式碼時定期執行圖層驗證，以便早期攔截相依性衝突。

### <a name="validate-code-from-an-open-dependency-diagram"></a>從開啟的相依性圖表驗證程式代碼

1. 以滑鼠右鍵按一下圖表介面，然後按一下 [ **驗證架構**]。

    > [!NOTE]
    > 根據預設，相依性圖表 ( .layerdiagram) 檔會設定 **為 [** **驗證** ]，讓圖表包含在驗證程式中。

     [ **錯誤清單** ] 視窗會報告發生的任何錯誤。 如需驗證錯誤的詳細資訊，請參閱 [疑難排解圖層驗證問題](#troubleshoot-layer-validation-issues)。

2. 若要查看每個錯誤的來源，請在 [ **錯誤清單** ] 視窗中按兩下錯誤。

    > [!NOTE]
    > Visual Studio 可能會顯示 code map，而不是錯誤的來源。 當程式碼相依于相依性圖表未指定的元件，或程式碼缺少相依性圖表所指定的相依性時，就會發生這種情況。 請檢閱 Code Map 或程式碼，以判斷相依性是否應存在。 如需 code map 的詳細資訊，請參閱 [對應整個方案](../modeling/map-dependencies-across-your-solutions.md)的相依性。

3. 若要管理錯誤，請參閱 [解決圖層驗證錯誤](#resolve-layer-validation-errors)。

### <a name="validate-code-at-the-command-prompt"></a>在命令提示字元中驗證程式代碼

1. 開啟 Visual Studio 命令提示字元。

2. 選擇下列其中之一：

   - 若要針對方案中的特定模型專案驗證程式代碼，請以下列自訂屬性執行 MSBuild。

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - 或 -

       流覽至包含模型專案的資料夾 ( modelingprojectfilenameandpath.modelproj) 檔和相依性圖表，然後以下列自訂屬性執行 MSBuild：

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - 若要針對方案中的所有模型專案驗證程式代碼，請以下列自訂屬性執行 MSBuild：

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - 或 -

       流覽至 [方案] 資料夾，其中必須包含包含相依性圖表的模型專案，然後使用下列自訂屬性執行 MSBuild：

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     發生的任何錯誤都將列出。 如需 MSBuild 的詳細資訊，請參閱 [msbuild](../msbuild/msbuild.md) 和 [msbuild](../msbuild/msbuild-task.md)工作。

   如需驗證錯誤的詳細資訊，請參閱 [疑難排解圖層驗證問題](#troubleshoot-layer-validation-issues)。

### <a name="manage-validation-errors"></a>管理驗證錯誤

在開發過程中，您可以隱藏驗證期間已報告過的某些衝突。 例如，您可能會想要隱藏已經處理的錯誤，或是與特定情節無關的錯誤。 當您隱藏錯誤時，在 Team Foundation 中記錄工作專案是很好的作法。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

#### <a name="create-a-work-item-for-a-validation-error"></a>建立驗證錯誤的工作專案

- 在 [ **錯誤清單** ] 視窗中，以滑鼠右鍵按一下錯誤、指向 [ **建立工作專案**]，然後按一下您要建立的工作專案類型。

您可以使用下列工作來管理 [ **錯誤清單** ] 視窗中的驗證錯誤：

|**若要**|**請依照下列步驟：**|
|-|-|
|在驗證期間隱藏選取的錯誤|以滑鼠右鍵按一下一或多個選取的錯誤，指向 [ **管理驗證錯誤**]，然後按一下 [ **隱藏錯誤**]。<br /><br /> 隱藏的錯誤會以刪除線的格式出現。 當您下一次執行驗證時，這些錯誤將不會出現。<br /><br /> 隱藏的錯誤會在對應相依性圖表檔案的隱藏檔案中追蹤。|
|停止隱藏選取的錯誤|以滑鼠右鍵按一下所選隱藏的錯誤或錯誤，指向 [ **管理驗證錯誤**]，然後按一下 [ **停止隱藏錯誤**]。<br /><br /> 選取的隱藏錯誤將會在下一次執行驗證時出現。|
|在 [ **錯誤清單** ] 視窗中還原所有隱藏的錯誤|以滑鼠右鍵按一下 [ **錯誤清單** ] 視窗中的任何位置，指向 [ **管理驗證錯誤**]，然後按一下 [ **顯示所有隱藏的錯誤**]。|
|從 [ **錯誤清單** ] 視窗隱藏所有隱藏的錯誤|以滑鼠右鍵按一下 [ **錯誤清單** ] 視窗中的任何位置，指向 [ **管理驗證錯誤**]，然後按一下 [ **隱藏所有隱藏的錯誤**]。|

## <a name="validate-code-automatically"></a>自動驗證程式碼

您可以在每次執行本機組建時執行圖層驗證。 如果您的小組使用 Azure DevOps，您可以使用閘道簽入來執行圖層驗證，您可以藉由建立自訂 MSBuild 工作來指定，以及使用組建報告來收集驗證錯誤。 若要建立閘道簽入組建，請參閱 [TFVC 閘道簽入](/azure/devops/pipelines/build/triggers)。

### <a name="to-validate-code-automatically-during-a-local-build"></a>在本機組建執行期間自動驗證程式碼

使用文字編輯器來開啟模型專案 (.modelproj) 檔案，然後加入下列屬性：

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- 或 -

1. 在 **方案總管** 中，以滑鼠右鍵按一下包含相依性圖表或圖表的模型專案，然後按一下 [ **屬性**]。

2. 在 [ **屬性** ] 視窗中，將模型專案的 [ **驗證架構** ] 屬性設定為 [ **True**]。

    這會將模型專案納入驗證程序中。

3. 在 **方案總管** 中，按一下您要用於驗證的相依性圖表 (. .layerdiagram) 檔。

4. 在 [ **屬性** ] 視窗中，確定圖表的 [ **組建動作** ] 屬性已設定為 [ **驗證**]。

    這包括驗證流程中的相依性圖表。

若要在 [錯誤清單] 視窗中管理錯誤，請參閱 [解決圖層驗證錯誤](#resolve-layer-validation-errors)。

## <a name="troubleshoot-layer-validation-issues"></a>疑難排解圖層驗證問題

下列表格描述圖層驗證的問題及其解決方式。 這些問題不同於因程式碼與設計衝突而導致的錯誤。 如需有關這些錯誤的詳細資訊，請參閱 [疑難排解圖層驗證問題](#troubleshoot-layer-validation-issues)。

|**問題**|**可能的原因**|**解決方法**|
|-|-|-|
|發生非預期的驗證錯誤。|當相依性圖表是從方案總管中的其他相依性圖表複製，而且在相同的模型專案中時，驗證無法運作。 以這種方式複製的相依性圖表會包含與原始相依性圖表相同的參考。|將新的相依性圖表加入至模型專案。<br /><br /> 將來源相依性圖表中的元素複製到新圖表。|

## <a name="resolve-layer-validation-errors"></a>解決圖層驗證錯誤

當您針對相依性圖表驗證程式代碼時，當程式碼與設計衝突時，就會發生驗證錯誤。 例如，下列條件可能造成圖層驗證發生錯誤：

- 成品指派給錯誤的圖層。 在此情況下，請移動成品。

- 類別之類的成品以與架構發生衝突的方式使用另一個類別。 在此情況下，請重構程式碼以移除相依性。

若要解決這些錯誤，請更新程式碼直到驗證時不再出現錯誤為止。 您可以透過互動方式執行這項工作。

以下章節說明用於這些錯誤的語法，解釋這些錯誤的意義，並且建議解析或管理這些錯誤的作法。

|**語法**|**說明**|
|-|-|
|*ArtifactN* (*ArtifactTypeN*) |*ArtifactN* 是與相依性圖表上的圖層相關聯的成品。<br /><br /> *ArtifactTypeN* 是 *ArtifactN* 的類型，例如 **類別** 或 **方法**，例如：<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|命名空間的名稱。|
|*LayerNameN*|相依性圖表上的圖層名稱。|
|*DependencyType*|*Artifact1* 和 *Artifact2* 之間的相依性關聯性類型。 例如， *Artifact1* 與 *Artifact2* 具有 **呼叫** 關聯性。|

| **錯誤語法。** | **錯誤描述** |
|-|-|
| DV0001：**無效** 的相依性 | 當對應至某個圖層的程式碼專案 (命名空間、類型、成員) 參考對應到另一個圖層的程式碼專案時，就會回報此問題，但相依性驗證圖表中包含此圖層的這些圖層之間沒有相依性箭號。 這是相依性條件約束違規。 |
| DV1001： **不正確命名空間名稱** | 此問題會在與圖層相關聯的程式碼元素上報告，而「允許的命名空間名稱」屬性不包含定義此程式碼專案的命名空間。 這是命名條件約束違規。 請注意，「允許的命名空間名稱」的語法是可定義關聯之程式碼專案的命名空間分號清單。 |
| DV1002：相依性 **unreferenceable 命名空間** | 此問題會在與圖層相關聯的程式碼元素上報告，並參考在此圖層的 "Unreferenceable Namespace" 屬性中定義的命名空間中定義的另一個程式碼專案。 這是命名條件約束違規。 請注意，"Unreferenceable 命名空間" 屬性定義為分號分隔的命名空間清單，不應在與此圖層相關聯的程式碼元素中參考。 |
| DV1003：不 **允許的命名空間名稱** | 此問題會在與圖層相關聯的程式碼元素上報告，其中「不允許的命名空間名稱」屬性包含定義此程式碼專案的命名空間。 這是命名條件約束違規。 請注意，[不允許的命名空間名稱] 屬性會定義為分號分隔的命名空間清單，而不應定義與此圖層相關聯的程式碼元素。 |
| DV2001： **圖層圖表存在** | 此問題會在不包含相依性圖表檔案的專案上報告，但會參考相依性驗證分析器。 如果尚未使用相依性驗證，您可以直接從方案總管移除 "DependencyValidation"，或隱藏此警告。 若要加入相依性圖表，請參閱 [從您的程式碼建立](../modeling/create-layer-diagrams-from-your-code.md)相依性圖表。 |
| DV2002：未對應的 **類型基底** | 當程式碼元素未對應到任何圖層時，就會回報此問題。 |
| DV3001： **遺漏連結** | 找不到 ' 成品 ' 圖 *層 '**LayerName*' 的連結。 您是否遺漏了組件參考? |
| DV9001： **架構分析發現內部錯誤** | 結果可能不完整。 如需詳細資訊，請參閱詳細建置事件記錄檔或輸出視窗。 |

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的即時相依性驗證](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)
- [影片：即時驗證您的架構相依性](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
