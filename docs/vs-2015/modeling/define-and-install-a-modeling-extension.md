---
title: 定義與安裝模型擴充功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: 82a58dc5-c7cf-4521-a6da-7ff09cd0de9d
caps.latest.revision: 39
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6f7895916cc4ee877c53b056f703d8e46b64b409
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805563"
---
# <a name="define-and-install-a-modeling-extension"></a>定義和安裝模型擴充功能
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

在 Visual Studio 中，您可以定義模型圖表的擴充功能。 使用這種方式，您可以調整圖表和模型，以符合您自己的需求。 例如，您可以定義功能表命令、UML 設定檔、驗證條件約束和工具箱項目。 您可以在單一擴充功能中定義數個元件。 您也可以使用 [Visual Studio 整合擴充功能 (VSIX)](http://go.microsoft.com/fwlink/?LinkId=160780)格式，將這些擴充功能散發給其他 Visual Studio 使用者。 您可以在 Visual Studio 中使用 VSIX 專案建立 VSIX。  
  
## <a name="requirements"></a>需求  
 請參閱 [需求](../modeling/extend-uml-models-and-diagrams.md#Requirements)。  
  
 若要查看哪些 Visual Studio 版本支援這項功能，請參閱 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)。  
  
## <a name="creating-a-modeling-extension-solution"></a>建立模型擴充功能方案  
 若要定義模型擴充功能，您必須建立包含這些專案的方案：  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 整合擴充功能 (VSIX) 專案。 這會產生做為您擴充功能元件之安裝程式的檔案。  
  
- 類別庫專案，包括程式碼之元件的必要項目。  
  
  如果您想要建立具有數個元件的擴充功能，則可以在單一方案中開發它們。 您只需要一個 VSIX 專案。  
  
  不需要程式碼的元件 (例如自訂工具箱項目和自訂 UML 設定檔) 可以直接加入 VSIX 專案，而不使用個別的類別庫專案。 需要程式碼的元件會更輕鬆地定義於個別的類別庫專案中。 需要程式碼的元件包括軌跡處理常式、功能表命令和驗證程式碼。  
  
#### <a name="to-create-a-class-library-project-for-menu-commands-gesture-handlers-or-validation"></a>建立功能表命令、軌跡處理常式或驗證的類別庫專案  
  
1.  在 [檔案]  功能表上，依序選擇 [新增] 和 [專案] 。  
  
2.  在 [已安裝的範本] 下，選取 [Visual C#]  或 [Visual Basic] ，然後選擇 [類別庫] 。  
  
#### <a name="to-create-a-vsix-project"></a>建立 VSIX 專案  
  
1.  如果您是使用程式碼建立元件，則最簡單的方式是先建立類別庫專案。 您會將您的程式碼加入該專案。  
  
2.  建立 VSIX 專案。  
  
    1.  在方案總管 中，於方案的捷徑功能表中，依序選擇 [加入] 和 [新增專案] 。  
  
    2.  在 [已安裝的範本] 下，展開 [Visual C#]  或 [Visual Basic] ，然後選取 [擴充性] 。 在中間的資料行中，選擇 [VSIX 專案] 。  
  
3.  將 VSIX 專案設定為方案的啟始專案。  
  
    -   在方案總管中，於 VSIX 專案的捷徑功能表上，選擇 [設定為啟始專案] 。  
  
4.  開啟 **source.extension.vsixmanifest**。 此檔案會在資訊清單編輯器中開啟。  
  
5.  在 [中繼資料]  索引標籤上，設定 VSIX 的名稱和描述欄位。  
  
6.  在 [安裝目標]  索引標籤上，選擇 [新增]  ，然後設定 Visual Studio 版本做為目標。  
  
7.  在 [資產]  索引標籤上，將您的元件加入 Visual Studio 擴充功能。  
  
    1.  選擇 [新增] 。  
  
    2.  針對使用程式碼的元件，在 [加入新資產]  對話方塊中設定這些欄位：  
  
        |||  
        |-|-|  
        |**型別** =|**Microsoft.VisualStudio.MefComponent**|  
        |**Source** =|**目前的方案中的專案**|  
        |**專案** =|*您的類別庫專案*|  
        |**嵌入此資料夾** =|*（空白）*|  
  
         對於其他元件類型，請參閱下一節中的連結。  
  
## <a name="developing-the-component"></a>開發元件  
 對於功能表命令或軌跡處理常式等每個元件，您必須定義個別的處理常式。 您可以將數個處理常式放在相同的類別庫專案。 下表摘要說明不同類型的處理常式。  
  
|擴充功能類型|主題|每個元件的一般宣告方式|  
|--------------------|-----------|----------------------------------------------|  
|功能表命令|[在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(ICommandExtension))]`<br /><br /> `public class MyCommand : ICommandExtension`<br /><br /> `{...`|  
|拖放或按兩下|[在模型圖表上定義軌跡處理常式](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md)|`[ClassDesignerExtension]`<br /><br /> `// or other diagram types`<br /><br /> `[Export(typeof(IGestureExtension))]`<br /><br /> `public class MyGesture : IGestureExtension`<br /><br /> `{...`|  
|驗證條件約束|[定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)|`[Export(typeof(     System.Action<ValidationContext, object>))]`<br /><br /> `[ValidationMethod(ValidationCategories.Save`<br /><br /> `&#124; ValidationCategories.Menu)]`<br /><br /> `public void ValidateSomething`<br /><br /> `(ValidationContext context, IClassifier elementToValidate)`<br /><br /> `{...}`|  
|工作項目連結事件處理常式|[定義工作項目連結處理常式](../modeling/define-a-work-item-link-handler.md)|`[Export(typeof(ILinkedWorkItemExtension))]`<br /><br /> `public class MyWorkItemEventHandler : ILinkedWorkItemExtension`<br /><br /> `{...`|  
|UML 設定檔|[定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)|(即將定義)|  
|工具箱項目|[定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)|(即將定義)|  
  
## <a name="running-an-extension-during-its-development"></a>在開發期間執行擴充功能  
  
#### <a name="to-run-an-extension-during-its-development"></a>在開發期間執行擴充功能  
  
1.  在  [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] **偵錯**功能表上，選擇 **開始偵錯**。  
  
     專案組建和新的 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 執行個體隨即使用實驗模式開啟。  
  
    -   或者，您可以選擇 [啟動但不偵錯] 。 這會減少啟動程式所需的時間。  
  
2.  在 Visual Studio 的實驗執行個體中建立或開啟模型專案，以及建立或開啟圖表。  
  
     您的擴充功能隨即載入和執行。  
  
3.  如果您使用 [啟動但不偵錯]  ，但想要使用偵錯工具，請回到 Visual Studio 的主要執行個體。 在 [偵錯]  功能表上，按一下 [附加至處理序] 。 在對話方塊中，選取具有程式名稱 **devenv**的 Visual Studio 實驗執行個體。  
  
##  <a name="Installing"></a> 安裝及解除安裝擴充功能  
 執行下列步驟，以在您自己的電腦或其他電腦上，於 Visual Studio 的主要執行個體中執行擴充功能。  
  
1.  在您的電腦中，尋找擴充功能專案所建置的 **.vsix** 檔案。  
  
    1.  在方案總管 中，於專案的捷徑功能表上，選擇 [在 Windows 檔案總管中開啟資料夾] 。  
  
    2.  找出檔案**筒\\\*\\**_YourProject_**.vsix**  
  
2.  將 **.vsix** 檔案複製到要安裝擴充功能的目標電腦。 這可以是您自己的電腦或其他電腦。  
  
    -   目標電腦必須有您在 **source.extension.vsixmanifest** 的 [安裝目標] 索引標籤中指定的其中一個 Visual Studio 版本。  
  
3.  在目標電腦上，開啟 **.vsix** 檔案 (例如，按兩下該檔案)。  
  
     [Visual Studio 擴充功能安裝程式] 隨即開啟並安裝擴充功能。  
  
4.  啟動或重新啟動 Visual Studio。  
  
#### <a name="to-uninstall-an-extension"></a>解除安裝擴充功能  
  
1. 在 [工具]  功能表上，按一下 [擴充功能和更新] 。  
  
2. 展開 [已安裝的擴充功能] 。  
  
3. 選取擴充功能，然後按一下 [解除安裝] 。  
  
   在很少見的情況下，故障的擴充功能無法載入並且會在錯誤視窗中建立報告，但不會顯示在擴充管理員中。 在此情況下，您可以移除延伸模組，從下列位置刪除檔案所在 *%localappdata%* 通常*DriveName*: \Users\\*的使用者名稱*\AppData\Local:  
  
   *%Localappdata%* **\Microsoft\VisualStudio\\[version] \Extensions**  
  
## <a name="see-also"></a>另請參閱  
 [定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)   
 [定義自訂模型工具箱項目](../modeling/define-a-custom-modeling-toolbox-item.md)   
 [定義 UML 模型的驗證條件約束](../modeling/define-validation-constraints-for-uml-models.md)   
 [在模型圖上定義功能表命令](../modeling/define-a-menu-command-on-a-modeling-diagram.md)



