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
ms.openlocfilehash: 483366fef0d736f4f1a0a98a027e7872f9c278da
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923613"
---
# <a name="validate-code-with-dependency-diagrams"></a>使用相依性圖表驗證程式碼

## <a name="why-use-dependency-diagrams"></a>為何要使用相依性圖表？

若要確定程式碼不會與其設計相衝突，以驗證程式碼在 Visual Studio 中的相依性圖表。 這可協助您：

- 在相依性圖表中找到您的程式碼中的相依性和相依性之間的衝突。

- 尋找可能會受到建議變更所影響的相依性。

   例如，您可以編輯相依性圖表來顯示可能的架構變更，並驗證程式碼，查看受影響的相依性。

- 將程式碼重構或移轉至不同設計。

   在您將程式碼移至不同的架構時，請尋找需要運作的程式碼或相依性。

**需求**

- Visual Studio

- 具有相依性圖表的模型專案的方案。 此相依性圖表必須連結到您想要驗證的 C# 或 Visual Basic 專案中的成品。 請參閱[從您的程式碼建立相依性圖表](../modeling/create-layer-diagrams-from-your-code.md)。

> [!NOTE]
> Visual Studio 2017 中的.NET Core 專案不支援相依性圖表。

若要查看哪些版本的 Visual Studio 支援此功能，請參閱[architecture and modeling tools 的版本支援](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

您可以驗證程式碼以手動方式從 Visual Studio 中開啟的相依性圖表，或從命令提示字元。 您也會自動驗證程式碼，執行本機組建或 Azure 管線組建時。 請參閱[Channel 9 影片：設計和驗證架構使用相依性圖表](http://go.microsoft.com/fwlink/?LinkID=252073)。

> [!IMPORTANT]
> 如果您想要執行使用 Team Foundation Server (TFS) 的圖層驗證，則您也必須在您的組建伺服器上安裝相同版本的 Visual Studio。

## <a name="live-dependency-validation"></a>即時相依性驗證

相依性驗證，就會發生即時和錯誤會立即顯示在**錯誤清單**。

* 即時驗證支援 C# 和 Visual Basic。

* 若要使用即時相依性驗證時，請啟用完整解決方案分析，開啟 [選項] 設定中會出現黃色提示列從**錯誤清單**。

   - 如果您不想要查看方案中的所有架構性問題，您可以永久關閉金色列。
   - 如果您未啟用完整解決方案分析，分析是為了只編輯的檔案。

* 升級時若要啟用即時驗證的專案，對話方塊會顯示轉換的進度。

* 更新時進行即時相依性驗證專案，NuGet 套件的版本升級至相同的所有專案，並是使用中的最高版本。

* 加入新的相依性驗證專案觸發專案更新。

## <a name="see-if-an-item-supports-validation"></a>查看項目是否支援驗證

您可以將圖層連結至網站、 Office 文件、 純文字檔案，與跨多個應用程式，共用的專案中的檔案，但驗證程序不包含這些。 對於連結至個別圖層之專案或組件的參考，如果這些圖層之間沒有任何相依性，則不會出現驗證錯誤。 除非程式碼使用這些參考，否則不會考量此類參考的相依性。

1.  在相依性圖表中，選取一或多個圖層，以滑鼠右鍵按一下您的選擇，然後按一下**檢視連結**。

2.  在 **圖層總管**，看看**支援驗證**資料行。 如果值為 false，則這個項目不支援驗證。

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>包含其他 .NET 組件和專案來進行驗證

當您將項目拖曳至相依性圖表時，對應的.NET 組件或專案的參考會自動加入至**圖層參考**模型專案中的資料夾。 這個資料夾包含組件的參考以及驗證期間分析的專案。 您可以包含其他.NET 組件和專案來進行驗證，而不需要以手動方式將它們拖曳至 相依性圖表。

1.  在**方案總管**，以滑鼠右鍵按一下模型專案或**圖層參考**資料夾，然後再按一下**加入參考**。

2.  在 [**加入參考**] 對話方塊中，選取組件或專案，然後按一下**確定**。

## <a name="validate-code-manually"></a>手動驗證程式碼

如果您有連結至方案項目開啟相依性圖表，您可以執行**驗證**從圖表的捷徑命令。 您也可以使用命令提示字元執行**msbuild**命令搭配**validatearchitecture**自訂的屬性設定為**True**。 例如，在您變更程式碼時定期執行圖層驗證，以便早期攔截相依性衝突。

### <a name="validate-code-from-an-open-dependency-diagram"></a>驗證程式碼，從開啟的相依性圖表

1.  以滑鼠右鍵按一下圖表介面，然後按一下**驗證架構**。

    > [!NOTE]
    > 根據預設，**建置動作**上的相依性圖表 (.layerdiagram) 檔案的屬性設定為**Validate** ，讓圖表納入驗證程序。

     **錯誤清單**視窗會報告所發生的任何錯誤。 如需有關驗證錯誤的詳細資訊，請參閱 <<c0> [ 了解並解決圖層驗證的錯誤](#UnderstandingValidationErrors)。

2.  若要檢視每個錯誤的來源，請連按兩下中的錯誤**錯誤清單**視窗。

    > [!NOTE]
    > Visual Studio 可能會顯示 code map，而不是錯誤的來源。 發生這種情況的程式碼不由相依性圖表中，指定的組件有相依性，或程式碼遺失相依性圖表中所指定的相依性時。 請檢閱 Code Map 或程式碼，以判斷相依性是否應存在。 如需 code map 的詳細資訊，請參閱[對應方案之間的相依性](../modeling/map-dependencies-across-your-solutions.md)。

3.  若要管理錯誤，請參閱[管理驗證錯誤](#ManageErrors)。

### <a name="validate-code-at-the-command-prompt"></a>驗證程式碼，在命令提示字元

1. 開啟 Visual Studio 命令提示字元。

2. 選擇下列其中一項：

   - 若要驗證對方案中的特定模型專案的程式碼，請使用下列自訂屬性執行 MSBuild。

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - 或 -

       瀏覽若資料夾包含模型專案 (.modelproj) 檔案和相依性圖表，然後執行 MSBuild 使用下列自訂屬性：

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - 若要驗證對方案中的所有模型專案的程式碼，請使用下列自訂屬性執行 MSBuild:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - 或 -

       瀏覽至方案資料夾內，且必須包含模型專案包含相依性圖表，然後執行 MSBuild，使用下列自訂屬性：

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     發生的任何錯誤都將列出。 如需 MSBuild 的詳細資訊，請參閱[MSBuild](../msbuild/msbuild.md)並[MSBuild 工作](../msbuild/msbuild-task.md)。

   如需有關驗證錯誤的詳細資訊，請參閱 <<c0> [ 了解並解決圖層驗證的錯誤](#UnderstandingValidationErrors)。

### <a name="manage-validation-errors"></a>管理驗證錯誤

在開發過程中，您可以隱藏驗證期間已報告過的某些衝突。 例如，您可能會想要隱藏已經處理的錯誤，或是與特定情節無關的錯誤。 當您隱藏錯誤時，最好還是 Team Foundation 中記錄的工作項目。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

#### <a name="create-a-work-item-for-a-validation-error"></a>建立驗證錯誤的工作項目

- 在 **錯誤清單**視窗中，以滑鼠右鍵按一下錯誤，指向**建立工作項目**，然後按一下您想要建立的工作項目類型。

使用這些工作來管理中的驗證錯誤**錯誤清單**視窗：

|**若要**|**請遵循下列步驟**|
|-|-|
|在驗證期間隱藏選取的錯誤|以滑鼠右鍵按一下一或多個選取的錯誤、 指向**管理驗證錯誤**，然後按一下**隱藏錯誤**。<br /><br /> 隱藏的錯誤會以刪除線的格式出現。 當您下一次執行驗證時，這些錯誤將不會出現。<br /><br /> 隱藏的錯誤會在對應的相依性圖表檔案的.suppressions 檔案追蹤。|
|停止隱藏選取的錯誤|以滑鼠右鍵按一下選取的隱藏的錯誤，並指向**管理驗證錯誤**，然後按一下**停止隱藏錯誤**。<br /><br /> 選取的隱藏錯誤將會在下一次執行驗證時出現。|
|還原所有隱藏的錯誤**錯誤清單**視窗|以滑鼠右鍵按一下任何一處**錯誤清單** 視窗中，指向**管理驗證錯誤**，然後按一下**顯示所有隱藏的錯誤**。|
|隱藏所有隱藏的錯誤**錯誤清單**視窗|以滑鼠右鍵按一下任何一處**錯誤清單** 視窗中，指向**管理驗證錯誤**，然後按一下**隱藏所有隱藏的錯誤**。|

## <a name="validate-code-automatically"></a>自動驗證程式碼

您可以在每次執行本機組建時執行圖層驗證。 如果您的小組會使用 Azure DevOps，您可以執行閘道簽入，藉由建立自訂的 MSBuild 工作和使用組建報告收集驗證錯誤，您可以指定圖層驗證。 若要建立閘道的簽入組建，請參閱[TFVC 閘道簽入](/azure/devops/pipelines/build/triggers#gated)。

### <a name="to-validate-code-automatically-during-a-local-build"></a>在本機組建執行期間自動驗證程式碼

使用文字編輯器來開啟模型專案 (.modelproj) 檔案，然後加入下列屬性：

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\-或-

1.  在 **方案總管**，以滑鼠右鍵按一下模型專案包含相依性圖表或圖表，然後按一下**屬性**。

2.  在 **屬性**視窗中，將模型專案的**驗證架構**屬性設**True**。

    這會將模型專案納入驗證程序中。

3.  在 [**方案總管] 中**，按一下您想要用於驗證的相依性圖表 (.layerdiagram) 檔案。

4.  中**屬性** 視窗中，請確定圖表**建置動作**屬性設定為**Validate**。

    這會將相依性圖表納入驗證程序。

若要管理 [錯誤清單] 視窗中的錯誤，請參閱[管理驗證錯誤](#ManageErrors)。

## <a name="troubleshoot-layer-validation-issues"></a>疑難排解圖層驗證問題

下列表格描述圖層驗證的問題及其解決方式。 這些問題不同於因程式碼與設計衝突而導致的錯誤。 如需有關這些錯誤的詳細資訊，請參閱 <<c0> [ 了解並解決圖層驗證的錯誤](#UnderstandingValidationErrors)。

|**問題**|**可能的原因**|**解決方法**|
|-|-|-|
|發生非預期的驗證錯誤。|驗證不適用於相依性圖表，會複製從方案總管 中的其他相依性圖表，以及屬於相同的模型專案中。 會在這種方式中複製的相依性圖表包含與原始的相依性圖表相同的參照。|將新的相依性圖表加入至模型專案。<br /><br /> 將來源的相依性圖表中的項目複製到新的圖表。|

## <a name="resolve-layer-validation-errors"></a>解決圖層驗證錯誤

當您驗證相依性圖表的程式碼時，程式碼設計發生衝突時，也會發生驗證錯誤。 例如，下列條件可能造成圖層驗證發生錯誤：

- 成品指派給錯誤的圖層。 在此情況下，請移動成品。

- 類別之類的成品以與架構發生衝突的方式使用另一個類別。 在此情況下，請重構程式碼以移除相依性。

若要解決這些錯誤，請更新程式碼直到驗證時不再出現錯誤為止。 您可以透過互動方式執行這項工作。

以下章節說明用於這些錯誤的語法，解釋這些錯誤的意義，並且建議解析或管理這些錯誤的作法。

|**語法**|**描述**|
|-|-|
|*ArtifactN*(*ArtifactTypeN*)|*ArtifactN*是相依性圖表的圖層相關聯的成品。<br /><br /> *ArtifactTypeN*是種*ArtifactN*，例如**類別**或是**方法**，例如：<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|命名空間的名稱。|
|*LayerNameN*|相依性圖表的圖層的名稱。|
|*DependencyType*|之間的相依性關聯性的類型*Artifact1*並*Artifact2*。 例如， *Artifact1*已**呼叫**關聯性*Artifact2*。|

| **錯誤語法** | **錯誤描述** |
|-|-|
| DV0001:**無效的相依性** | 當程式碼項目 （命名空間、 類型與成員） 對應至圖層參考對應到另一個圖層的程式碼項目，但這些相依性驗證圖表，其中包含此圖層中的圖層之間沒有任何相依性箭號時，會報告此問題。 這是相依性條件約束違規。 |
| DV1001:**無效的命名空間名稱** | 此問題會回報 「 允許的命名空間名稱 」 屬性不包含此程式碼項目定義所在的命名空間的圖層相關聯的程式碼項目。 這是命名的條件約束違規。 請注意，「 允許的命名空間名稱 」 的語法是以分號分隔的清單其中程式碼與相關聯的項目是圖層的命名空間被允許定義。 |
| DV1002:**不可參考的命名空間上的相依性** | 此問題會回報與圖層關聯及參考圖層的 「 不可參考命名空間 」 屬性中定義的命名空間中定義的另一個程式碼項目，程式碼項目。 這是命名的條件約束違規。 請注意，「 不可參考命名空間 」 屬性定義為以分號分隔清單，不應在此圖層相關聯的程式碼項目中參考的命名空間。 |
| DV1003:**不允許的命名空間名稱** | 此問題會回報 「 不允許的命名空間名稱 」 屬性包含此程式碼項目定義所在的命名空間的圖層相關聯的程式碼項目。 這是命名的條件約束違規。 請注意，「 不允許命名空間名稱 」 屬性定義為以分號分隔清單在哪一個程式碼中與此圖層相關聯的項目不應定義的命名空間。 |
| DV3001:**遺失的連結** | 圖層 '*LayerName*'連結到'*成品*' 找不到其中。 您是否遺漏了組件參考? |
| DV9001:**架構分析發現內部錯誤** | 結果可能不完整。 如需詳細資訊，請參閱詳細建置事件記錄檔或輸出視窗。 |

## <a name="see-also"></a>另請參閱

- [Visual Studio 2017 中的即時相依性驗證](https://blogs.msdn.microsoft.com/devops/2016/11/30/live-dependency-validation-in-visual-studio-2017/)
- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)
- [影片：驗證即時架構相依性](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)