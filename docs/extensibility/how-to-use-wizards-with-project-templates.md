---
title: "如何：搭配專案範本使用精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IWizard 介面"
  - "專案範本 [Visual Studio], 精靈"
  - "範本 [Visual Studio], 精靈"
  - "Visual Studio 範本, 精靈"
  - "精靈 [Visual Studio], 專案範本"
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：搭配專案範本使用精靈
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 會提供 Visual Studio 介面，這個介面在實作後，可以讓您在使用者從範本建立專案時執行自訂的程式碼。  
  
 專案範本自訂可以用於：  
  
-   顯示會收集使用者輸入以參數化範本的自訂 UI。  
  
-   加入要在範本中使用的參數值。  
  
-   將其他檔案加入範本。  
  
-   在專案上執行 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Automation 物件模型所允許的大部分動作。  
  
 建立專案時，會在不同的時間點呼叫 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面方法，而且只要使用者按一下 \[**新增專案**\] 對話方塊上的 \[**確定**\]，就會開始呼叫。  介面的每個方法是以描述呼叫方法的時間點來命名。  例如，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會在開始建立專案時立即呼叫 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>，使它成為撰寫自訂程式碼以收集使用者輸入的好位置。  
  
 您為自訂精靈所撰寫的大部分程式碼，將使用 <xref:EnvDTE.DTE> 物件 \(它是 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Automation 物件模型中的主要物件\) 來自訂專案。  如需 Automation 物件模型的詳細資訊，請參閱[擴充 Visual Studio 環境](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)和[Automation 與擴充性參考](../Topic/Automation%20and%20Extensibility%20Reference.md)。  
  
## 建立自訂範本精靈  
 本主題顯示如何建立會在專案建立之前開啟 Windows Form 的自訂精靈。  此表單可以讓使用者加入自訂參數值，而此參數值將在建立專案時加入至原始程式碼。  主要的步驟一一詳述如下。  
  
#### 若要建立自訂範本精靈  
  
1.  建立實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的組件。  
  
2.  將組件安裝到全域組件快取。  
  
3.  建立專案並使用 \[**匯出範本**\] 精靈，從專案建立範本。  
  
4.  在 .vstemplate 檔案中加入 `WizardExtension` 項目以修改範本，使範本連結至實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的組件。  
  
5.  使用自訂精靈建立新專案。  
  
## 實作 IWizard  
 處理過程中的第一個步驟是建立實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的組件。  這個組件會使用 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法顯示 Windows Form，以便讓使用者加入在建立專案時將使用到的自訂參數值。  
  
> [!NOTE]
>  這個範例使用 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 來實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>，不過您也可以使用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]。  
  
#### 若要實作 IWizard  
  
1.  建立新的類別庫專案。  
  
2.  建立實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的類別。  請參閱下面完整實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 範例程式碼。  
  
 這個範例包含兩個程式碼檔案：`IWizardImplementation` 是實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的類別，而 `UserInputForm` 是讓使用者輸入的 Windows Form。  
  
### IWizardImplementation 類別  
 `IWizardImplementation` 類別包含 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的每個成員的方法實作。  在這個範例中，只有 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法會執行工作。  其他所有方法不執行任何工作，或是只傳回 `true`。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> 方法接受四個參數：  
  
-   <xref:System.Object> 參數，可以轉型為 <xref:EnvDTE._DTE> 根物件，讓您可以自訂專案。  
  
-   <xref:System.Collections.Generic.Dictionary%602> 參數，包含範本中所有預先定義的參數集合。  如需範本參數的詳細資訊，請參閱[樣板參數](../ide/template-parameters.md)。  
  
-   <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind> 參數，包含所使用的範本的相關資訊。  
  
-   <xref:System.Object> 陣列，包含由 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 傳遞給精靈的參數集合。  
  
 這個範例會從使用者輸入表單中，將參數值加入 <xref:System.Collections.Generic.Dictionary%602> 參數。  專案中 `$custommessage$` 參數的每個執行個體將以使用者輸入的文字取代。  您必須將下列配件加入至專案：  
  
1.  EnvDTE.dll  
  
2.  Microsoft.VisualStudio.TemplateWizardInterface.dll  
  
3.  System.Windows.Forms.dll  
  
> [!IMPORTANT]
>  這個範例中使用的 UserInputForm 在下列章節中定義。  
  
```c#  
using System;  
using System.Collections.Generic;  
using Microsoft.VisualStudio.TemplateWizard;  
using System.Windows.Forms;  
using EnvDTE;  
  
namespace CustomWizard  
{  
    public class IWizardImplementation:IWizard  
    {  
        private UserInputForm inputForm;  
        private string customMessage;  
  
        // This method is called before opening any item that   
        // has the OpenInEditor attribute.  
        public void BeforeOpeningFile(ProjectItem projectItem)  
        {  
        }  
  
        public void ProjectFinishedGenerating(Project project)  
        {  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public void ProjectItemFinishedGenerating(ProjectItem   
            projectItem)  
        {  
        }  
  
        // This method is called after the project is created.  
        public void RunFinished()  
        {  
        }  
  
        public void RunStarted(object automationObject,  
            Dictionary<string, string> replacementsDictionary,  
            WizardRunKind runKind, object[] customParams)  
        {  
            try  
            {  
                // Display a form to the user. The form collects   
                // input for the custom message.  
                inputForm = new UserInputForm();  
                inputForm.ShowDialog();  
  
                customMessage = inputForm.get_CustomMessage();  
  
                // Add custom parameters.  
                replacementsDictionary.Add("$custommessage$",   
                    customMessage);  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show(ex.ToString());  
            }  
        }  
  
        // This method is only called for item templates,  
        // not for project templates.  
        public bool ShouldAddProjectItem(string filePath)  
        {  
            return true;  
        }          
    }  
}  
```  
  
### 使用者輸入表單  
 使用者輸入表單會提供一個輸入自訂參數的簡單表單。  表單中包含名為 `textBox1` 的文字方塊，以及名為 `button1` 的按鈕。  當按一下按鈕時，來自文字方塊的文字便會儲存在 `customMessage` 參數中。  
  
##### 若要將 Windows Form 加入方案  
  
1.  將下列程式碼加入至內含精靈插件的檔案。  
  
```c#  
public partial class UserInputForm : Form  
{  
    private string customMessage;  
    private TextBox textBox1;  
  
    public UserInputForm()  
    {   
        textBox1 = new TextBox();  
        this.Controls.Add(textBox1);  
    }  
  
    public string get_CustomMessage()  
    {  
        return customMessage;  
    }  
  
    private void textBox1_TextChanged(object sender, EventArgs e)  
    {  
        customMessage = textBox1.Text;  
        this.Dispose();  
    }  
}  
```  
  
## 將組件安裝到全域組件快取  
 實作 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 的組件必須以強式名稱簽署，並安裝到全域組件快取。  
  
#### 若要將組件安裝到全域組件快取中  
  
1.  使用強式名稱簽署組件。  如需詳細資訊，請參閱 [如何：使用強式名稱簽署組件](../Topic/How%20to:%20Sign%20an%20Assembly%20with%20a%20Strong%20Name.md)或[How to: Sign an Assembly \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/f468a7d3-234c-4353-924d-8e0ae5896564)。  
  
2.  將強式名稱的組件安裝到全域組件快取中。  如需詳細資訊，請參閱[如何：將組件安裝到全域組件快取](../Topic/How%20to:%20Install%20an%20Assembly%20into%20the%20Global%20Assembly%20Cache.md)。  
  
## 建立要當做範本使用的專案  
 在這個範本中，當做範本使用的專案是一個主控台應用程式，它會顯示在自訂精靈的使用者輸入表單中所指定的訊息。  
  
#### 若要建立範本專案  
  
1.  建立新的 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] 主控台應用程式。  
  
2.  在應用程式的 `Main` 方法中，加入下列程式碼行。  
  
    ```  
    Console.WriteLine("$custommessage$");  
    ```  
  
     當從範本建立專案時，`$custommessage$` 參數會以使用者輸入表單中所輸入的文字取代。  
  
3.  按一下 \[**檔案**\] 功能表上的 \[**匯出範本**\]。  
  
4.  在 \[**匯出範本**\] 精靈中，按一下 \[**專案範本**\]，選取正確的專案，然後按一下 \[**下一步**\]。  
  
5.  在 \[**匯出範本**\] 精靈中，輸入關於範本的描述性資訊，選取 \[**自動將範本匯入 Visual Studio**\] 核取方塊，然後按一下 \[**完成**\]。  
  
     範本現在會顯示在 \[**新增專案**\] 對話方塊中，但是不會使用自訂精靈。  
  
 下列範例會顯示匯出成範本之前的完整程式碼檔。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
namespace TemplateProject  
{  
    class WriteMessage  
    {  
        static void Main(string[] args)  
        {  
            Console.WriteLine("$custommessage$");  
        }  
    }  
}  
```  
  
## 修改範本  
 現在範本已經建立並顯示在 \[**新增專案**\] 對話方塊中，您必須加以修改，讓它使用您在前面的步驟中所建立的組件。  
  
#### 若要將自訂精靈加入範本  
  
1.  尋找包含範本的 .zip 檔。  
  
    1.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
    2.  按一下 \[**專案和方案**\]。  
  
    3.  閱讀 \[**Visual Studio 使用者專案範本位置**\] 文字方塊。  
  
     依據預設，這個位置為 My Documents\\Visual Studio *Version*\\Templates\\ProjectTemplates。  
  
2.  解壓縮這個 .zip 檔。  
  
3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中開啟 .vstemplate 檔。  
  
4.  在 `TemplateContent` 項目後面，加入 [WizardExtension 項目 \(Visual Studio 範本\)](../extensibility/wizardextension-element-visual-studio-templates.md) 項目及自訂精靈組件的強式名稱。  如需尋找組件的強式名稱的詳細資訊，請參閱 [如何：檢視全域組件快取的內容](../Topic/How%20to:%20View%20the%20Contents%20of%20the%20Global%20Assembly%20Cache.md)和 [如何：參考強式名稱簽署組件](../Topic/How%20to:%20Reference%20a%20Strong-Named%20Assembly.md)。  
  
     下列範例會顯示 `WizardExtension` 項目。  
  
    ```  
    <WizardExtension>  
        <Assembly>CustomWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=fa3902f409bb6a3b</Assembly>  
        <FullClassName>CustomWizard.IWizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
## 使用自訂精靈  
 現在您可以從範本建立專案，並使用自訂精靈。  
  
#### 若要使用自訂精靈  
  
1.  在 \[檔案\] 功能表上，按一下 \[新增專案\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，找出您的範本，並輸入名稱，然後按一下 \[**確定**\]。  
  
     精靈使用者輸入表單便會開啟。  
  
3.  輸入自訂參數的值，然後按一下按鈕。  
  
     精靈使用者輸入表單便會關閉，同時會從範本建立專案。  
  
4.  在 \[**方案總管**\] 中，在原始程式碼檔上按一下滑鼠右鍵，並按一下 \[**檢視程式碼**\]。  
  
     請注意，`$custommessage$` 會以在精靈使用者輸入表單中所輸入的文字取代。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 項目 \(Visual Studio 範本\)](../extensibility/wizardextension-element-visual-studio-templates.md)