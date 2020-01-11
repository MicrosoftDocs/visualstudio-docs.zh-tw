---
title: 如何：建立特定領域語言方案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4c5bd99c47517156f1ec89de9da1a163223b99a
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850441"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：建立網域指定的語言方案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

特定領域語言（DSL）是使用特製化的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 解決方案所建立。

## <a name="prerequisites"></a>必要條件：
 開始進行此程式之前，您必須先安裝下列元件：

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](https://docs.microsoft.com/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](https://docs.microsoft.com/samples/browse/?redirectedfrom=MSDN-samples)|

## <a name="creating-a-domain-specific-language-solution"></a>建立特定領域語言方案

#### <a name="to-create-a-domain-specific-language-solution"></a>若要建立特定領域語言方案

1. 啟動 DSL Wizard。

   1. 在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。

   2. [ **新增專案** ] 對話方塊隨即出現。

   3. 在 [**專案類型**] 底下，展開 [**其他專案類型**] 節點，**然後按一下 [** 擴充性]。

   4. 按一下 [**網域指定的語言設計**工具]。

   5. 在 [**名稱**] 方塊中，輸入解決方案的名稱。 按一下 [ **確定**]。

       **定義域指定的語言設計工具 Wizard**隨即出現。

      > [!NOTE]
      > 您輸入的名稱最好是有效的視覺C#識別碼，因為它可能會用來產生程式碼。

      ![建立 DSL 對話方塊](../modeling/media/create-dsldialog.png "Create_DSLDialog")

2. 選擇 DSL 範本。

    在 [**選取網域特定語言選項**] 頁面上，選取其中一個方案範本，例如 [**最小語言**]。 選擇類似您想要建立之 DSL 的範本。

    如需解決方案範本的詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

3. 在 [**副檔名**] 頁面上輸入檔案名副檔名。 在您的電腦上，以及您要安裝 DSL 的任何電腦上，它應該是唯一的。 您應該會看到 [**沒有任何應用程式或 Visual Studio 編輯器使用此延伸**模組] 訊息。

   - 如果您已在先前的實驗性 Dsl 中使用尚未完整安裝的副檔名，您可以使用 [**重設實驗實例**] 工具將其清除，這可在 [[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK] 功能表中找到。

   - 如果您的電腦已完整安裝使用此副檔名的另一個 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組，請考慮將它卸載。 在 [**工具**] 功能表上，按一下 [**擴充管理員**]。

4. 檢查並視需要調整 wizard 其餘頁面中的欄位。 當您對設定感到滿意時，請按一下 **[完成]** 。 如需設定的詳細資訊，請參閱[DSL 設計工具 Wizard 頁面](#settings)。

    此 wizard 會建立一個方案，其中包含兩個名為**Dsl**和**DslPackage**的專案。

   > [!NOTE]
   > 如果您看到一則訊息，提醒您不要從不受信任的來源執行文字模板，請按一下 **[確定]** 。 您可以設定此訊息，不要再次出現。

## <a name="settings"></a>DSL 設計工具 Wizard 頁面
 您可以讓數個欄位的預設值保持不變。 不過，請確定您已設定 [副檔名] 欄位。

### <a name="solution-settings-page"></a>解決方案設定頁面
 **您想要以何種範本作為特定領域語言的基礎？**
選擇類似您想要建立之 DSL 的範本。 不同的範本提供了方便的起點。 當您選取解決方案範本時，嚮導會顯示描述。 如需解決方案範本的詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

 **您要將特定領域語言命名為什麼？**
預設為解決方案名稱。 此值會產生程式碼。 它必須是有效的C#類別名稱。

### <a name="file-extension-page"></a>[副檔名] 頁面
 **模型檔案使用哪個延伸模組？**
輸入新的副檔名。

 確認此副檔名尚未在此電腦上註冊以供使用，如下所示：

 查看 [**其他已註冊的工具和應用程式]，以處理此延伸**模組。 如果您看到 [**沒有任何應用程式或 Visual Studio 編輯器使用此延伸**模組] 訊息，則可以使用此副檔名。

 如果您看到工具或套件的清單，您應該執行下列其中一項動作：

- 輸入不同的副檔名。

     \-或-

- 重設 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 實驗實例。 這會取消註冊您先前建立的所有 Dsl。 在 [**開始**] 功能表上，依序按一下 [**所有程式**]、[ **Microsoft Visual Studio 2010 SDK**] 和 [**工具**]，然後**重設 Microsoft Visual Studio 2010 實驗實例**。 您可以重建任何其他您想要再次使用的 Dsl。

     \-或-

- 如果您的電腦已完整安裝使用此副檔名的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 延伸模組，請將它卸載。 在 [**工具**] 功能表上，按一下 [**擴充管理員**]。

### <a name="product-settings-page"></a>[產品設定] 頁面
 **新的特定領域語言所屬的產品名稱是什麼？**
預設為 DSL 名稱。

 這個值會在 Windows Explorer （或檔案瀏覽器）中用來描述具有此副檔名的檔案。

 **產品所屬公司的名稱為何？**
您的公司名稱。

 這個值會併入 DSL 套件的 AssemblyInfo 屬性中。

 **此解決方案中專案的根命名空間是什麼？**
這會預設為從您的公司和產品名稱組成的名稱。

### <a name="signing-page"></a>簽署頁面
 **建立強式名稱金鑰**檔預設選項是建立新的金鑰來簽署 DSL 元件。

 **使用現有的強式名稱金鑰**如果您想要整合 DSL 與另一個元件，請使用此選項。

 如需強式命名的詳細資訊，請參閱[建立和使用強式名稱的元件](https://docs.microsoft.com/dotnet/standard/assembly/create-use-strong-named?redirectedfrom=MSDN)。

## <a name="see-also"></a>請參閱
 [如何定義特定領域語言的](../modeling/how-to-define-a-domain-specific-language.md)[網域特定語言工具詞彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
