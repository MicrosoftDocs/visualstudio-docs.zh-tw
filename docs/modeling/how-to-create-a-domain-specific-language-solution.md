---
title: "如何： 建立特定領域語言方案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 5adfe90d88f46f4a3c31c1ddb6eb860403d57fe4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2018
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：建立網域指定的語言方案
特定領域語言 (DSL) 由使用特殊[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]方案。  
  
## <a name="prerequisites"></a>必要條件  
 您可以啟動此程序之前，您必須先安裝這些元件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK||  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
## <a name="creating-a-domain-specific-language-solution"></a>建立特定領域語言方案  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>若要建立特定領域語言方案  
  
1.  啟動 DSL 精靈。  
  
    1.  在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
    2.  [ **新增專案** ] 對話方塊隨即出現。  
  
    3.  在下**專案類型**，依序展開**其他專案類型**節點，然後按一下**擴充性**。  
  
    4.  按一下**網域特定語言設計工具**。  
  
    5.  在**名稱**方塊中，輸入方案的名稱。 按一下 [確定 **Deploying Office Solutions**]。  
  
         **網域特定語言設計工具精靈**隨即出現。  
  
        > [!NOTE]
        >  最好是您所輸入的名稱應該是有效的 Visual C# 識別項，因為它可能會用來產生程式碼。  
  
     ![[建立 DSL] 對話方塊](../modeling/media/create_dsldialog.png "Create_DSLDialog")  
  
2.  選擇 DSL 範本。  
  
     在**選取特定領域語言選項**頁面上，選取其中一個解決方案範本，例如**基本語言**。 選擇您想要建立 DSL 類似的範本。  
  
     如需解決方案範本的詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
3.  在輸入檔案的副檔名**副檔名**頁面。 應該是唯一的電腦中，您想要安裝 DSL 所在的任何電腦中。 您應該會看到訊息**沒有應用程式或 Visual Studio 編輯器使用此延伸模組**。  
  
    -   如果您使用先前未完整安裝的實驗 Dsl 中的檔案名稱副檔名，您可以清除它們出使用**重設實驗執行個體**工具，可以在找到[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]SDK 功能表。  
  
    -   如果另一個[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組使用此副檔名的完整安裝在電腦上，請考慮解除安裝它。 在**工具**功能表上，按一下 **擴充管理員**。  
  
4.  檢查，並視調整，請在精靈的其餘頁面中的欄位。 當您設定完成後，請按一下**完成**。 如需設定的詳細資訊，請參閱[DSL 設計工具的精靈頁面](#settings)。  
  
     精靈會建立一個具有兩個專案，名為方案**Dsl**和**DslPackage**。  
  
    > [!NOTE]
    >  如果您看到訊息，提醒您不受信任來源執行文字範本，請按一下**確定**。 您可以設定此訊息不會再出現。  
  
##  <a name="settings"></a>DSL 設計工具的精靈頁面  
 您可以保留不變，從其預設值的欄位數。 不過，請確定您設定檔案延伸模組欄位。  
  
### <a name="solution-settings-page"></a>方案 [設定] 頁面  
 **您要根據您的網域特定語言的範本？**  
 選擇您想要建立 DSL 類似的範本。 不同的範本會提供方便的起點。 當您選取的解決方案範本時，精靈會顯示描述。 如需解決方案範本的詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 **要命名您的特定領域語言？**  
 預設為方案名稱。 這個值產生程式碼。 它必須是有效做為 C# 類別名稱。  
  
### <a name="file-extension-page"></a>副檔名頁面  
 **哪些延伸模組應該建立的模型檔案使用嗎？**  
 輸入新的副檔名。  
  
 驗證，此副檔名已尚未註冊用於此電腦，如下所示：  
  
 查看 **其他工具和應用程式登錄來處理這項擴充功能**。 如果您看到 「**沒有應用程式或 Visual Studio 編輯器使用此延伸模組**，則您可以使用這個副檔名。  
  
 如果您看到工具或封裝的清單，您應該執行下列其中一項：  
  
-   輸入不同的檔案副檔名。  
  
     \-或-  
  
-   重設[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]實驗執行個體。 這會將所有您先前建立的 Dsl 取消登錄。 在**啟動**功能表上，按一下 **所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設Microsoft Visual Studio 2010 實驗執行個體**。 您可以重建您想要一次使用的任何其他 Dsl。  
  
     \-或-  
  
-   如果[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]延伸模組使用此副檔名的完整安裝在電腦上，解除安裝。 在**工具**功能表上，按一下 **擴充管理員**。  
  
### <a name="product-settings-page"></a>產品 [設定] 頁面  
 **新的網域特定語言所屬的產品名稱為何？**  
 預設值是 DSL 名稱。  
  
 使用此值是在 Windows 檔案總管 （或檔案總管） 來描述此副檔名的檔案。  
  
 **產品所屬的公司名稱為何？**  
 您的公司名稱。  
  
 這個值會併入的 DSL 封裝 AssemblyInfo 屬性。  
  
 **什麼是這個方案中專案的根命名空間？**  
 預設值為 由您的公司名稱和產品名稱。  
  
### <a name="signing-page"></a>簽署頁  
 **建立強式名稱金鑰檔案**  
 若要建立新的金鑰來簽署您 DSL 的組件是預設選項。  
  
 **使用現有的強式名稱金鑰**  
 如果您想要整合 DSL 與另一個組件，請使用此選項。  
  
 如需有關強式命名的詳細資訊，請參閱[Creating and using strong-named Assemblies](http://go.microsoft.com/fwlink/?LinkId=186073)。  

## <a name="see-also"></a>另請參閱

[如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)  
[特定領域語言工具詞彙](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
