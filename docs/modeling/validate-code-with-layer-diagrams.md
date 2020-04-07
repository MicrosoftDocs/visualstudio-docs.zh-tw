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
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 975fe8eac5657e245027a4811e50bbc93528cfe5
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759696"
---
# <a name="validate-code-with-dependency-diagrams"></a>使用相依性圖表驗證程式碼

## <a name="why-use-dependency-diagrams"></a>為什麼要使用依賴關係關係圖?

為了確保代碼不與其設計衝突,請使用 Visual Studio 中的依賴關係圖驗證代碼。 這可協助您：

- 查找代碼中的依賴項與依賴關係關係關係圖的依賴項之間的衝突。

- 尋找可能會受到建議變更所影響的相依性。

   例如,您可以編輯依賴關係關係圖以顯示潛在的體系結構更改,然後驗證代碼以查看受影響的依賴項。

- 將程式碼重構或移轉至不同設計。

   在您將程式碼移至不同的架構時，請尋找需要運作的程式碼或相依性。

**需求**

- Visual Studio

  要為 .NET Core 專案創建依賴關係關係圖,必須具有 Visual Studio 2019 版本 16.2 或更高版本。

- 具有具有依賴關係關係圖的建模專案的解決方案。 此依賴關係關係圖必須連結到要驗證的 C# 或 Visual Basic 專案中的專案。 請參考[此程式碼建立相依關係的關係圖](../modeling/create-layer-diagrams-from-your-code.md)。

要檢視哪些版本的 Visual Studio 支援此功能,請參閱[版本支援架構結構和建模工具](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。

可以從 Visual Studio 中的打開依賴關係圖或命令提示符手動驗證代碼。 您還可以在執行本地生成或 Azure 管道產生時自動驗證代碼。 請參閱[第 9 頻道視訊:使用相依關係關係圖設計和驗證體系結構](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)。

> [!IMPORTANT]
> 如果要使用團隊基礎伺服器 (TFS) 執行圖層驗證,還必須在生成伺服器上安裝相同版本的 Visual Studio。

## <a name="live-dependency-validation"></a>即時相依項驗證

相依項驗證即時,錯誤會立即顯示在**錯誤清單中**。

* 支援 C# 和可視化基本版的即時驗證。

* 要在使用即時依賴項驗證時啟用完整的解決方案分析,請使用**錯誤列表**中顯示的金條打開選項設置。

  - 如果您對解決方案中的所有體系結構問題不感興趣,則可以永久關閉金條。
  - 如果不啟用完整的解決方案分析,則僅針對正在編輯的檔執行分析。

* 升級專案以啟用即時驗證時,將顯示轉換的進度。

* 更新專案進行即時依賴項驗證時,NuGet 包的版本將升級為對所有專案相同,並且是正在使用的最高版本。

* 添加新的依賴項驗證專案將觸發專案更新。

## <a name="see-if-an-item-supports-validation"></a>查看項目是否支援驗證

您可以將圖層連結到網站、Office 文檔、純文本檔和跨多個應用共用的專案中的檔,但驗證過程不包括它們。 對於連結至個別圖層之專案或組件的參考，如果這些圖層之間沒有任何相依性，則不會出現驗證錯誤。 除非程式碼使用這些參考，否則不會考量此類參考的相依性。

1. 在依賴關係關係圖上,選擇一個或多個圖層,右鍵單擊您的選擇,然後按一下「**查看連結**」。

2. 在**層資源管理員中**,查看 **「支援驗證」** 欄位。 如果值為 false，則這個項目不支援驗證。

## <a name="include-other-net-assemblies-and-projects-for-validation"></a>包含其他 .NET 組件和專案來進行驗證

將專案拖動到依賴關係關係圖時,對相應的 .NET 程式集或專案的引用將自動添加到建模專案中的 **「圖層引用」** 資料夾中。 這個資料夾包含組件的參考以及驗證期間分析的專案。 您可以包括其他 .NET 程式集和專案進行驗證,而無需手動將它們拖動到依賴關係關係圖。

1. 在**解決方案資源管理員**中,右鍵單擊建模專案或**圖層引用**資料夾,然後單擊「**添加參考**」。

2. 在"**添加參考"** 對話方塊中,選擇裝配體或項目,然後單擊"**確定**"。

## <a name="validate-code-manually"></a>手動驗證程式碼

如果有連結到解決方案項的開放依賴關係關係圖,則可以從關係圖運行 **「驗證**快捷方式」命令。 您還可以使用指令提示符執行**msbuild**指令,將 **/p:驗證體系結構**自訂屬性設定為**True**。 例如，在您變更程式碼時定期執行圖層驗證，以便早期攔截相依性衝突。

### <a name="validate-code-from-an-open-dependency-diagram"></a>從開啟的相依關係的圖驗證碼

1. 右鍵單擊關係圖曲面,然後單擊 **「驗證體系結構**」。。

    > [!NOTE]
    > 預設情況下,依賴關係關係圖 (.layer 關係圖) 檔案上的**生成操作**屬性設置為 **『驗證**』,以便該關係圖包含在驗證過程中。

     錯誤**清單「** 視窗報告發生的任何錯誤」。 有關驗證錯誤的詳細資訊,請參閱[排除層驗證問題。](#troubleshoot-layer-validation-issues)

2. 要檢視每個錯誤的源,請在 **「錯誤列表」** 視窗中按兩下錯誤。

    > [!NOTE]
    > Visual Studio 可能會顯示代碼映射,而不是錯誤源。 當代碼對依賴關係關係圖未指定的程式集具有依賴項,或者代碼缺少依賴關係關係圖指定的依賴項時,將發生這種情況。 請檢閱 Code Map 或程式碼，以判斷相依性是否應存在。 有關程式映射的詳細資訊,請參閱[解決方案中的對應相依項 。](../modeling/map-dependencies-across-your-solutions.md)

3. 要管理錯誤,請參閱[解決圖層驗證錯誤](#resolve-layer-validation-errors)。

### <a name="validate-code-at-the-command-prompt"></a>在命令提示符號驗證程式碼

1. 打開視覺化工作室命令提示符。

2. 選擇下列其中之一：

   - 要根據解決方案中的特定建模項目驗證代碼,請使用以下自定義屬性運行 MSBuild。

       ```
       msbuild <FilePath+ModelProjectFileName>.modelproj /p:ValidateArchitecture=true
       ```

     - 或 -

       瀏覽到包含建模專案 (.modelproj) 檔案和相依關係關係圖的資料夾,然後使用以下自訂屬性執行 MSBuild:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

   - 要針對解決方案中的所有建模項目驗證代碼,請使用以下自訂屬性運行 MSBuild:

       ```
       msbuild <FilePath+SolutionName>.sln /p:ValidateArchitecture=true
       ```

     - 或 -

       瀏覽到解決方案資料夾,該資料夾必須包含包含依賴關係關係圖的建模項目,然後使用以下自訂屬性運行 MSBuild:

       ```
       msbuild /p:ValidateArchitecture=true
       ```

     發生的任何錯誤都將列出。 有關 MSBuild 的詳細資訊,請參閱[MSBuild](../msbuild/msbuild.md)和[MSBuild 任務](../msbuild/msbuild-task.md)。

   有關驗證錯誤的詳細資訊,請參閱[排除層驗證問題。](#troubleshoot-layer-validation-issues)

### <a name="manage-validation-errors"></a>管理驗證錯誤

在開發過程中，您可以隱藏驗證期間已報告過的某些衝突。 例如，您可能會想要隱藏已經處理的錯誤，或是與特定情節無關的錯誤。 當您抑制錯誤時,最好在團隊基礎中記錄工作項。

> [!WARNING]
> 您必須先連接 TFS 原始程式碼控制 (SCC) 才能建立或連結工作項目。 若您嘗試開啟連接至不同的 TFS SCC，Visual Studio 會自動關閉目前方案。 請先確認您已連接至適當的 SCC，再嘗試建立或連結至工作項目。 在更新版本的 Visual Studio 中，如果沒有連接至 SCC 即無法使用功能表命令。

#### <a name="create-a-work-item-for-a-validation-error"></a>為驗證錯誤建立工作項目

- 在 **「錯誤清單」** 視窗中,右鍵單擊錯誤,指向 **「創建工作項**」,然後單擊要創建的工作項的類型。

使用這些工作在 **「錯誤清單」** 視窗中管理驗證錯誤:

|**自**|**按照以下步驟操作**|
|-|-|
|在驗證期間隱藏選取的錯誤|右鍵按一個或多個選定的錯誤,指向**管理驗證錯誤**,然後單擊 **「禁止錯誤**」。。<br /><br /> 隱藏的錯誤會以刪除線的格式出現。 當您下一次執行驗證時，這些錯誤將不會出現。<br /><br /> 在相應的依賴關係關係圖檔中跟蹤抑制錯誤。|
|停止隱藏選取的錯誤|右鍵按一下選取的抑制錯誤或錯誤,指向**管理驗證錯誤**,然後單擊「**停止禁止錯誤**」。。<br /><br /> 選取的隱藏錯誤將會在下一次執行驗證時出現。|
|在 **'錯誤列表'** 視窗中還原所有已抑制的錯誤|右鍵按**下 「錯誤清單」** 視窗中的任意位置,指向 **「管理驗證錯誤**」,然後按下「**顯示所有壓縮錯誤**」 。|
|從**錯誤清單「 視窗**隱藏所有已抑制的錯誤|右鍵按**下 「錯誤清單」** 視窗中的任意位置,指向 **「管理驗證錯誤**」,然後按下 **「 隱藏所有抑制錯誤**」。|

## <a name="validate-code-automatically"></a>自動驗證程式碼

您可以在每次執行本機組建時執行圖層驗證。 如果團隊使用 Azure DevOps,則可以使用封閉簽入執行圖層驗證,可以通過創建自訂 MSBuild 任務來指定該值,並使用生成報告收集驗證錯誤。 要建立門控簽入產生,請參閱[TFVC 門控簽入](/azure/devops/pipelines/build/triggers)。

### <a name="to-validate-code-automatically-during-a-local-build"></a>在本機組建執行期間自動驗證程式碼

使用文字編輯器來開啟模型專案 (.modelproj) 檔案，然後加入下列屬性：

```xml
<ValidateArchitecture>true</ValidateArchitecture>
```

\- 或 -

1. 在**解決方案資源管理員**中,右鍵按一下包含相依關係的圖或關聯式建模項目,**然後單擊屬性**。

2. 在 **「屬性」** 視窗中,將建模項目的 **「驗證體系結構」** 屬性設定為**True**。

    這會將模型專案納入驗證程序中。

3. 在**解決方案資源管理員中**,單擊要用於驗證的依賴關係圖 (.layer 關係圖)檔。

4. 在 **「屬性」** 視窗中,請確保關係圖的**生成操作**屬性設置為 **「驗證**」。

    這包括驗證過程中的依賴關係圖。

在「錯誤清單」 視窗中管理錯誤,請參閱[解決圖層驗證錯誤](#resolve-layer-validation-errors)。

## <a name="troubleshoot-layer-validation-issues"></a>疑難排解圖層驗證問題

下列表格描述圖層驗證的問題及其解決方式。 這些問題不同於因程式碼與設計衝突而導致的錯誤。 有關這些錯誤的詳細資訊,請參閱[排除層驗證問題。](#troubleshoot-layer-validation-issues)

|**問題**|**可能的原因**|**解析度**|
|-|-|-|
|發生非預期的驗證錯誤。|驗證不適用於從解決方案資源管理器中的其他依賴關係關係關係圖複製且位於同一建模專案中的依賴關係關係關係圖。 以這種方式複製的依賴關係關係圖包含與原始依賴關係關係圖相同的引用。|向建模專案添加新的依賴關係關係圖。<br /><br /> 將元素從源依賴關係關係關係圖複製到新關係圖。|

## <a name="resolve-layer-validation-errors"></a>解決層驗證錯誤

當您根據依賴關係關係圖驗證代碼時,當代碼與設計衝突時,將發生驗證錯誤。 例如，下列條件可能造成圖層驗證發生錯誤：

- 成品指派給錯誤的圖層。 在此情況下，請移動成品。

- 類別之類的成品以與架構發生衝突的方式使用另一個類別。 在此情況下，請重構程式碼以移除相依性。

若要解決這些錯誤，請更新程式碼直到驗證時不再出現錯誤為止。 您可以透過互動方式執行這項工作。

以下章節說明用於這些錯誤的語法，解釋這些錯誤的意義，並且建議解析或管理這些錯誤的作法。

|**語法**|**說明**|
|-|-|
|*工件N*(*工件類型N*)|*工件N*是與依賴關係關係圖上的圖層關聯的專案。<br /><br /> *工件類型N*是*工件N*的類型,例如**類別**或**方法**,例如:<br /><br /> MySolution.MyProject.MyClass.MyMethod(Method)|
|*NamespaceNameN*|命名空間的名稱。|
|*LayerNameN*|依賴關係關係圖上圖層的名稱。|
|*DependencyType*|*專案 1*和*工件 2*之間的依賴關係類型。 例如,*工件1*與*工件2*具有**調用**關係。|

| **錯誤語法。** | **錯誤說明** |
|-|-|
| DV0001:**不合法的依賴項** | 當映射到圖層的代碼元素(命名空間、類型、成員)引用映射到另一個圖層的代碼元素時,將報告此問題,但在包含此圖層的依賴項驗證圖中這些圖層之間沒有依賴關係箭頭。 這是依賴項約束衝突。 |
| DV1001:**不合法的命名空間名稱** | 此問題報告在與"允許命名名稱"屬性不包含定義此代碼元素的命名空間的層關聯的代碼元素上。 這是命名約束衝突。 請注意,「允許的命名名稱」的語法是允許定義與圖層關聯的代碼元素的命名空間的分號清單。 |
| DV1002:**對不可參考命名空間的相依** | 此問題報告在與圖層關聯的代碼元素上,並引用在命名空間中定義的另一個代碼元素,該代碼元素在圖層的"不可引用命名空間"屬性中定義。 這是命名約束衝突。 請注意,"不可引用的命名空間"屬性定義為不應在與此圖層關聯的代碼元素中引用的命名空間的分號分隔清單。 |
| DV1003:**不允許命名空間名稱** | 此問題報告在與"不允許命名名稱"屬性包含定義此代碼元素的命名空間的圖層關聯的代碼元素上。 這是命名約束衝突。 請注意,"不允許命名空間名稱"屬性定義為不應在此層關聯的代碼元素的命名空間的分號分隔清單。 |
| DV2001:**層圖存在** | 此問題報告在不包含依賴關係關係關係關係圖檔但引用依賴項驗證分析器的專案上。 如果未使用依賴項驗證,則可以直接從解決方案資源管理器中刪除「Microsoft.依賴驗證.分析器」或禁止此警告。 要新增相依關係關係的資訊,請參閱[從代碼建立相依關係關係的圖](../modeling/create-layer-diagrams-from-your-code.md)。 |
| DV2002:**未映射型別庫** | 當代碼元素未映射到任何圖層時,將報告此問題。 |
| DV3001:**缺少連結** | 層次 「*圖層名稱*」 連結到找不到的 *「 工件*」 。 您是否遺漏了組件參考? |
| DV9001:**架構分析發現內部錯誤** | 結果可能不完整。 如需詳細資訊，請參閱詳細建置事件記錄檔或輸出視窗。 |

## <a name="see-also"></a>另請參閱

- [視覺化工作室中的即時相依項驗證](https://devblogs.microsoft.com/devops/live-dependency-validation-in-visual-studio-2017/)
- [在開發期間驗證您的系統](../modeling/validate-your-system-during-development.md)
- [視訊:即時驗證體系結構依賴關係](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
