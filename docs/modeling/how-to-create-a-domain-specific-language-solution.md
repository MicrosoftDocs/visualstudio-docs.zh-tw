---
title: 如何：建立網域指定的語言方案
description: 瞭解如何使用特製化的 Visual Studio 解決方案， (DSL) 建立特定領域語言。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c913f3015c56f7872dfe5ef3471578de7075b7d0
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363272"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：建立網域指定的語言方案
特定領域語言 (DSL) 是使用特製化的 Visual Studio 解決方案所建立。

## <a name="prerequisites"></a>Prerequisites

開始此程式之前，請先安裝下列元件：

- Visual Studio
- Visual Studio SDK (安裝為 **Visual Studio 延伸模組開發** 工作負載的一部分) 
- 模型 SDK (安裝為 Visual Studio 元件) 

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="creating-a-domain-specific-language-solution"></a>建立 Domain-Specific 語言方案

1. 藉由建立新的 **特定領域語言設計工具** 專案，啟動 DSL Wizard。

   > [!NOTE]
   > 您為專案選擇的名稱最好是有效的 Visual c # 識別碼，因為它可能會用來產生程式碼。

   ::: moniker range="vs-2017"

   ![[建立 DSL] 對話方塊](../modeling/media/create_dsldialog.png)

   ::: moniker-end

2. 選擇 DSL 範本。

    在 [ **選取 Domain-Specific 語言選項** ] 頁面上，選取其中一個解決方案範本，例如 **最基本的語言**。 選擇與您想要建立的 DSL 類似的範本。

    如需解決方案範本的詳細資訊，請參閱 [選擇 Domain-Specific 語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

3. 在 [ **副檔名** ] 頁面上輸入副檔名。 在您的電腦中，以及您想要安裝 DSL 的任何電腦中，它應該是唯一的。 您應該會看到 **沒有任何應用程式或 Visual Studio 編輯器使用此延伸** 模組的訊息。

   - 如果您在先前的實驗性 Dsl 中使用了尚未完整安裝的副檔名，則可以使用 [ **重設實驗實例** ] 工具（可在 Visual Studio SDK 功能表中找到）來清除它們。

   - 如果您的電腦已完整安裝使用此副檔名的另一個 Visual Studio 擴充功能，請考慮將其卸載。 按一下 [ **工具** ] 功能表上的 [ **擴充管理員**]。

4. 檢查並視需要調整嚮導其餘頁面中的欄位。 當您對設定感到滿意後，請按一下 **[完成]**。 如需設定的詳細資訊，請參閱 [DSL 設計工具 Wizard 頁面](#settings)。

    此 wizard 會建立一個方案，其中包含兩個名為 **Dsl** 和 **DslPackage** 的專案。

   > [!NOTE]
   > 如果您看到一則訊息，提醒您不要從不受信任的來源執行文字模板，請按一下 **[確定]**。 您可以將此訊息設定為不會再次出現。

## <a name="the-dsl-designer-wizard-pages"></a><a name="settings"></a> DSL 設計工具 Wizard 頁面
 您可以將數個欄位的預設值維持不變。 不過，請確定您已設定 [副檔名] 欄位。

### <a name="solution-settings-page"></a>解決方案設定頁面
 **您要將哪個範本作為網域特定語言的基礎？**
選擇與您想要建立的 DSL 類似的範本。 不同的範本會提供便利的起點。 當您選取方案範本時，嚮導會顯示描述。 如需解決方案範本的詳細資訊，請參閱 [選擇 Domain-Specific 語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。

 **您想要為特定領域語言命名什麼？**
預設為方案名稱。 從這個值產生程式碼。 它必須是有效的 c # 類別名稱。

### <a name="file-extension-page"></a>副檔名頁面
 **哪些延伸模組應該使用模型檔案？**
輸入新的副檔名。

 確認此副檔名尚未在這部電腦上註冊使用，如下所示：

 查看 **已註冊的其他工具和應用程式，以處理此延伸** 模組。 如果您看到 [ **沒有應用程式] 或 Visual Studio 編輯器使用此延伸** 模組，則可以使用此副檔名。

 如果您看到工具或封裝的清單，則應該執行下列其中一項：

- 輸入不同的副檔名。

     \- 或 -

- 重設 Visual Studio 實驗實例。 這會取消註冊您先前建立的所有 Dsl。 在 [ **開始** ] 功能表上，按一下 [ **所有程式**]、 **Microsoft Visual Studio 2010 SDK**]、[ **工具**]，然後 **重設 Microsoft Visual Studio 2010 實驗實例**。 您可以重建您想要再次使用的任何其他 Dsl。

     \- 或 -

- 如果您的電腦已完整安裝使用此副檔名的 Visual Studio 延伸模組，請將它卸載。 按一下 [ **工具** ] 功能表上的 [ **擴充管理員**]。

### <a name="product-settings-page"></a>產品設定頁面
 **新網域特定語言所屬的產品名稱為何？**
預設為 DSL 名稱。

 此值會在 Windows 檔案總管 (或檔案總管) 中用來描述具有此副檔名的檔案。

 **產品所屬公司的名稱為何？**
您的公司名稱。

 此值會併入 DSL 套件的 AssemblyInfo 屬性中。

 **此解決方案中專案的根命名空間為何？**
這預設為由您的公司和產品名稱組成的名稱。

### <a name="signing-page"></a>簽署頁面
 **建立強式名稱金鑰** 檔預設選項是建立新的金鑰來簽署 DSL 元件。

 **使用現有的強式名稱金鑰** 如果您想要將 DSL 與另一個元件整合，請使用此選項。

 如需強式命名的詳細資訊，請參閱 [建立和使用 Strong-Named 元件](/dotnet/standard/assembly/create-use-strong-named)。

## <a name="see-also"></a>請參閱

- [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)
- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)