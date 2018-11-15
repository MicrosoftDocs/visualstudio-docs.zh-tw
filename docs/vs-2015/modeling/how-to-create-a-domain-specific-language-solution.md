---
title: 如何： 建立特定領域語言解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.designerwizard
helpviewer_keywords:
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools], creating domain-specific language
- Domain-Specific Language Tools, creating solutions
ms.assetid: e585b63b-34d2-405a-8d81-39ea22317975
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2650afc2172cdcceca892d4ad19a05becac3e472
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908910"
---
# <a name="how-to-create-a-domain-specific-language-solution"></a>如何：建立網域指定的語言方案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

特定領域語言 (DSL) 由使用特殊化[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]解決方案。  
  
## <a name="prerequisites"></a>必要條件  
 您可以啟動此程序之前，您必須先安裝這些元件：  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-a-domain-specific-language-solution"></a>建立特定領域語言方案  
  
#### <a name="to-create-a-domain-specific-language-solution"></a>若要建立特定領域語言方案  
  
1. 啟動 [DSL] 精靈。  
  
   1. 在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。  
  
   2. [ **新增專案** ] 對話方塊隨即出現。  
  
   3. 底下**專案類型**，展開**其他專案類型**節點，然後按一下**擴充性**。  
  
   4. 按一下  **Domain-specific Language Designer**。  
  
   5. 在 **名稱**方塊中，輸入方案的名稱。 按一下 [確定 **Deploying Office Solutions**]。  
  
       **Domain-specific Language Designer 精靈**隨即出現。  
  
      > [!NOTE]
      >  最好是您所輸入的名稱應該是有效的 Visual C# 識別項，因為它可能會用來產生程式碼。  
  
      ![建立 DSL 對話方塊](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
2. 選擇 DSL 」 範本。  
  
    在 **選取特定領域語言選項**頁面上，選取其中一個解決方案範本類似**最小語言**。 選擇的範本，類似於您想要建立 DSL。  
  
    如需解決方案範本的詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
3. 輸入檔案的副檔名**副檔名**頁面。 它應該是唯一的電腦，並在其上的任何電腦在您想要安裝 DSL。 您應該會看到訊息**沒有應用程式或 Visual Studio 編輯器會使用此延伸模組**。  
  
   -   如果您已使用的副檔名，未完整安裝的上一個實驗 Dsl 中，您可以清除它們出利用**重設實驗執行個體**工具，可在[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]SDK 功能表。  
  
   -   如果另一個[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]已完整延伸模組，可使用這個副檔名在電腦上安裝，請考慮解除安裝它。 在 **工具**功能表上，按一下**延伸模組管理員**。  
  
4. 檢查，以及必要時調整，請在精靈的其餘頁面中的欄位。 當您滿意設定時，請按一下**完成**。 如需有關設定的詳細資訊，請參閱[DSL 設計工具的精靈頁面](#settings)。  
  
    精靈會建立具有兩個專案，名為的解決方案**Dsl**並**DslPackage**。  
  
   > [!NOTE]
   >  如果您看到訊息，向您發出警示不執行文字範本來自不受信任的來源，請按一下**確定**。 您可以設定此訊息不會再出現。  
  
##  <a name="settings"></a> DSL 設計工具的精靈頁面  
 您可以保留預設值未變更的欄位數。 不過，請確定您設定副檔名欄位。  
  
### <a name="solution-settings-page"></a>解決方案設定頁面  
 **您要根據您的網域特定語言的範本？**  
 選擇的範本，類似於您想要建立 DSL。 不同的範本會提供便利的起點。 當您選取的解決方案範本時，精靈就會顯示描述。 如需解決方案範本的詳細資訊，請參閱[選擇特定領域語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 **要命名您的網域特定語言？**  
 預設為方案名稱。 與這個值會產生程式碼。 它必須是有效的 C# 類別名稱。  
  
### <a name="file-extension-page"></a>檔案延伸模組頁面  
 **哪些項擴充功能模型檔案應該使用？**  
 輸入新的副檔名。  
  
 確認，這個副檔名已經尚未註冊用於此電腦，如下所示：  
  
 查看底下**其他工具和應用程式註冊處理這個副檔名**。 如果您看到訊息**沒有應用程式或 Visual Studio 編輯器會使用此延伸模組**，則您可以使用此副檔名。  
  
 如果您看到一份工具或封裝，您應該執行下列其中一項：  
  
-   輸入不同的檔案副檔名。  
  
     \-或-  
  
-   重設[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]實驗執行個體。 這將會取消註冊所有您先前建立的 Dsl。 在上**開始**功能表上，按一下**所有程式**， **Microsoft Visual Studio 2010 SDK**，**工具**，然後**重設Microsoft Visual Studio 2010 Experimental 執行個體**。 您可以重建任何其他您想要再次使用的 Dsl。  
  
     \-或-  
  
-   如果[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]已完整延伸模組，可使用這個副檔名在電腦上安裝、 解除安裝它。 在 **工具**功能表上，按一下**延伸模組管理員**。  
  
### <a name="product-settings-page"></a>產品 [設定] 頁面  
 **新特定領域語言所屬產品的名稱為何？**  
 預設為 DSL 的名稱。  
  
 此值可在 Windows 檔案總管 （或檔案總管） 來描述此副檔名的檔案。  
  
 **產品所屬公司的名稱為何？**  
 您的公司名稱。  
  
 這個值會併入您的 DSL 封裝的 AssemblyInfo 屬性。  
  
 **什麼是這個方案中專案的根命名空間？**  
 預設為組成您公司的名稱和產品名稱。  
  
### <a name="signing-page"></a>簽署頁  
 **建立強式名稱金鑰檔**  
 預設選項是建立新的金鑰來簽署您的 DSL 組件。  
  
 **使用現有的強式名稱金鑰**  
 如果您想要整合您的 DSL 使用另一個組件，請使用此選項。  
  
 如需有關強式命名的詳細資訊，請參閱 <<c0> [ 建立和使用強式名稱組件](http://go.microsoft.com/fwlink/?LinkId=186073)。  
  
## <a name="see-also"></a>另請參閱  
 [如何定義特定領域語言](../modeling/how-to-define-a-domain-specific-language.md)   
 [特定領域語言工具字彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



