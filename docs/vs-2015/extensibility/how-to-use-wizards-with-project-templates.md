---
title: 如何： 搭配專案範本使用精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 650b9c360013d06216e607269f77afd24f3cc22c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783749"
---
# <a name="how-to-use-wizards-with-project-templates"></a>如何：搭配專案範本使用精靈
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 提供<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面，這個介面實作時，可讓您執行自訂程式碼，當使用者從範本建立專案。  
  
 專案範本自訂可用來顯示專案中收集使用者輸入，以自訂範本、 將其他檔案新增至範本，或是允許的任何其他動作的自訂 UI。  
  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>在專案建立時，只要使用者按一下啟動不同時間呼叫介面方法**確定**上**新專案** 對話方塊。 介面的每個方法稱為來描述處呼叫它的點。 例如，Visual Studio 會呼叫<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>立即開始建立專案時，使得撰寫自訂程式碼，來收集使用者輸入的理想位置。  
  
## <a name="creating-a-project-template-project-with-a-vsix-project"></a>使用 VSIX 專案建立專案範本專案  
 您開始建立自訂的範本與專案範本的專案，這是 Visual Studio SDK 的一部分。 在此程序中，我們將使用 C# 專案範本的專案，但也是 Visual Basic 專案範本專案。 然後您加入 VSIX 專案包含專案範本專案的方案。  
  
1.  建立 C# 專案範本的專案 (在 Visual Studio 中，**檔案 / 新增 / 專案 / Visual C# / 擴充性 / C# 專案範本**)。 命名**MyProjectTemplate**。  
  
    > [!NOTE]
    >  系統可能會要求您安裝 Visual Studio SDK。 如需詳細資訊，請參閱 <<c0> [ 安裝 Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md)。  
  
2.  加入新的 VSIX 專案 (**檔案 / 新增 / 專案 / Visual C# / 擴充性 / VSIX 專案**) 相同的方案與專案範本專案中 (在**方案總管 中**，選取 解決方案 節點中，按一下滑鼠右鍵，然後選取**新增 / 新增專案**)。 它命名為**MyProjectWizard。**  
  
3.  將 VSIX 專案設定為啟始專案。 在 **方案總管**，選取方案節點、 按一下滑鼠右鍵，然後選取**設定為啟始專案**。  
  
4.  範本將專案加入做為 VSIX 專案的資產。 中**方案總管**、 VSIX 專案節點下，尋找**source.extension.vsixmanifest**檔案。 按兩下以在資訊清單編輯器中開啟它。  
  
5.  在資訊清單編輯器中，選取**資產**視窗左側的索引標籤。  
  
6.  在 **資產**索引標籤上，選取**新增**。 在 [**加入新資產**] 視窗中的型別欄位中，選取**Microsoft.VisualStudio.ProjectTemplate**。 在 **來源**欄位中，選取**目前方案中的專案**。 在 **專案**欄位中，選取**MyProjectTemplate**。 然後按一下 [確定]。   
  
7.  建置方案並開始偵錯。 Visual Studio 的第二個執行個體隨即出現。 （這可能需要幾分鐘的時間）。  
  
8.  在 Visual Studio 的第二個執行個體，嘗試使用新的範本建立新的專案。 (**檔案 / 新增 / 專案 / Visual C# / MyProject 範本**)。 使用名為類別的新的專案應該會出現**Class1**。 您現在已建立自訂專案範本 ！ 現在停止偵錯。  
  
## <a name="creating-a-custom-template-wizard"></a>建立自訂範本精靈  
 本主題說明如何建立自訂精靈建立專案之前開啟 Windows 表單。 表單可讓使用者加入自訂參數值在專案建立期間新增至原始程式碼。  
  
1. 設定 VSIX 專案，以允許它建立組件。  
  
2. 在 [**方案總管] 中**，選取 [VSIX 專案] 節點。 下面 [方案總管] 中，您應該看到**屬性**視窗。 如果您不這樣做，請選取**檢視 / 屬性 視窗**，或按**F4**。 在 屬性 視窗中，選取 在下列欄位`true`:  
  
   -   **IncludeAssemblyInVSIXContainer**  
  
   -   **IncludeDebugSymbolsInVSIXContainer**  
  
   -   **IncludeDebugSymbolsInLocalVSIXDeployment**  
  
3. 做為資產中加入 VSIX 專案的組件。 開啟 source.extension.vsixmanifest 檔案中，然後選取**資產** 索引標籤。中**加入新資產** 視窗中，如**型別**選取**Microsoft.VisualStudio.Assembly**，如**來源**選取**的目前方案中的專案**，並針對**專案**選取**MyTemplateWizard**。  
  
4. 將下列參考加入 VSIX 專案。 (在**方案總管**，在 VSIX 專案節點，選取**參考**，按一下滑鼠右鍵，然後選取**加入參考**。)在 **加入參考**對話方塊，請在**Framework**索引標籤上，尋找**System.Windows 表單**組件並加以選取。 現在，選取**延伸模組** 索引標籤尋找**EnvDTE**組件並加以選取。 也會發現**Microsoft.VisualStudio.TemplateWizardInterface**組件並加以選取。 按一下 [確定 **Deploying Office Solutions**]。  
  
5. 加入 VSIX 專案的精靈實作的類別。 (在 方案總管 中，以滑鼠右鍵按一下 VSIX 專案節點，然後選取**新增**，然後**新項目**，然後**類別**。)將類別命名為**WizardImplementation**。  
  
6. 中的程式碼取代**WizardImplementationClass.cs**為下列程式碼的檔案：  
  
   ```csharp  
   using System;  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.TemplateWizard;  
   using System.Windows.Forms;  
   using EnvDTE;  
  
   namespace MyProjectWizard  
   {  
       public class WizardImplementation:IWizard  
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
  
                   customMessage = UserInputForm.CustomMessage;  
  
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
  
    **UserInputForm**參考此程式碼將可較晚實作。  
  
    `WizardImplementation`類別包含的每個成員的方法實作<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>。 在此範例中，只有<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>方法執行的工作。 所有其他方法會執行任何動作，或傳回`true`。  
  
    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>方法接受四個參數：  
  
   - <xref:System.Object>參數，就可以轉換成根<xref:EnvDTE._DTE>物件，可讓您自訂的專案。  
  
   - A<xref:System.Collections.Generic.Dictionary%602>參數，其中包含在範本中的所有預先定義參數的集合。 如需有關範本參數的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。  
  
   - A<xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>參數，其中包含要使用何種範本的相關資訊。  
  
   - <xref:System.Object> Visual studio 包含一組參數的陣列傳遞給精靈。  
  
     這個範例會從使用者輸入表單，以加入的參數值<xref:System.Collections.Generic.Dictionary%602>參數。 每個執行個體`$custommessage$`專案中的參數將會取代使用者所輸入的文字。 您必須在您的專案中新增下列組件：  
  
7. 現在，建立**UserInputForm**。 在  **WizardImplementation.cs**檔案中，新增下列程式碼結束後**WizardImplementation**類別。  
  
   ```csharp  
   public partial class UserInputForm : Form  
       {  
           private static string customMessage;  
           private TextBox textBox1;  
           private Button button1;  
  
           public UserInputForm()  
           {  
               this.Size = new System.Drawing.Size(155, 265);   
  
               button1 = new Button();  
               button1.Location = new System.Drawing.Point(90, 25);  
               button1.Size = new System.Drawing.Size(50, 25);  
               button1.Click += button1_Click;  
               this.Controls.Add(button1);  
  
               textBox1 = new TextBox();  
               textBox1.Location = new System.Drawing.Point(10, 25);  
               textBox1.Size = new System.Drawing.Size(70, 20);  
               this.Controls.Add(textBox1);  
           }  
           public static string CustomMessage  
           {  
               get  
               {  
                   return customMessage;  
               }  
               set  
               {  
                   customMessage = value;  
               }     
           }  
           private void button1_Click(object sender, EventArgs e)  
           {  
               customMessage = textBox1.Text;  
           }  
       }  
   ```  
  
    使用者輸入的表單提供一個簡單的表單輸入的自訂參數。 此表單包含名為文字方塊`textBox1`和名為按鈕`button1`。 當按一下按鈕時，從文字方塊中的文字會儲存在`customMessage`參數。  
  
## <a name="connect-the-wizard-to-the-custom-template"></a>連接至自訂範本的精靈  
 為了讓您自訂專案範本，若要使用您自訂的精靈，您需要登入精靈 的組件，並將一些行新增至您的自訂專案範本，讓它知道哪裡可以找到精靈的實作，建立新的專案時。  
  
1. 簽署組件。 在 **方案總管**，選取 VSIX 專案、 按一下滑鼠右鍵，然後選取**專案屬性**。  
  
2. 在 [**專案屬性**視窗中，選取**簽署**] 索引標籤中的**簽署**索引標籤上，勾選**簽署組件**。 在 **選擇強式名稱金鑰檔**欄位中，選取**\<新增 >**。 在 [**建立強式名稱金鑰**] 視窗，請在**金鑰檔名稱**欄位中，輸入**key.snk**。 取消核取**保護我的密碼金鑰檔**欄位。  
  
3. 在 **方案總管**，選取 VSIX 專案，並尋找**屬性**視窗。  
  
4. 設定**複製組建輸出到輸出目錄**欄位設為 **，則為 true**。 這可讓組件，以重新建置方案時，會複製到輸出目錄。 它仍然包含在.vsix 檔案。 您需要查看組件，以便了解其簽署金鑰。  
  
5. 重建方案。  
  
6. 您現在可以在 MyProjectWizard 專案目錄中尋找的 key.snk 檔案 (**\<磁碟位置 > \MyProjectTemplate\MyProjectWizard\key.snk**)。 將複製的 key.snk 檔案。  
  
7. 移至輸出目錄，並尋找組件 (**\<磁碟位置 > \MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll**)。 貼上以下的 key.snk 檔案。 （這並非絕對必要，但它會讓下列步驟輕鬆）。  
  
8. 開啟命令視窗，並將在其中建立組件的目錄。  
  
9. 尋找**sn.exe**簽署工具。 比方說，Windows 10 64 位元作業系統上，典型的路徑會是下列：  
  
     **C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools**  
  
     如果找不到工具，請嘗試執行**其中 /R。 sn.exe**命令視窗中。 記下路徑。  
  
10. 從 key.snk 檔案中擷取的公開金鑰。 在 [命令] 視窗中，輸入  
  
     **\<sn.exe 的位置 > \sn.exe-p key.snk outfile.key。**  
  
     別忘了用 sn.exe 加上引號的路徑，如果目錄名稱中有空格 ！  
  
11. 從 outfile 取得的公開金鑰語彙基元：  
  
     **\<sn.exe 的位置 > \sn.exe-t outfile.key。**  
  
     同樣地，別忘了引號。 您應該會看到如下的輸出中的資料行  
  
     **公開金鑰語彙基元是 <token>**  
  
     記下此值。  
  
12. 自訂精靈的參考加入專案範本的.vstemplate 檔中。 在 [方案總管] 中，尋找名為 MyProjectTemplate.vstemplate，檔案並開啟它。 結束後\<TemplateContent > 區段中，新增下列區段：  
  
    ```xml  
    <WizardExtension>  
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>  
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>  
    </WizardExtension>  
    ```  
  
     其中**MyProjectWizard**是名稱的組件，並**語彙基元**是您在上一個步驟中複製的權杖。  
  
13. 儲存在專案中的所有檔案，並重建。  
  
## <a name="adding-the-custom-parameter-to-the-template"></a>將自訂參數新增至範本  
 在此範例中，做為範本的專案會顯示自訂精靈的使用者輸入表單中指定的訊息。  
  
1. 在 [方案總管] 中，移至**MyProjectTemplate**專案，然後開啟**Class1.cs**。  
  
2. 在 `Main`方法的應用程式中，新增下列程式碼行。  
  
   ```  
   Console.WriteLine("$custommessage$");  
   ```  
  
    參數`$custommessage$`會取代從範本建立專案時，使用者輸入表單中輸入的文字。  
  
   以下是完整的程式碼檔案，才能匯出成範本。  
  
```csharp  
using System;  
using System.Collections.Generic;  
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;  
$endif$using System.Text;  
  
namespace $safeprojectname$  
{  
    public class Class1  
    {  
          static void Main(string[] args)  
          {  
               Console.WriteLine("$custommessage$");  
          }  
    }  
}  
```  
  
## <a name="using-the-custom-wizard"></a>使用自訂的精靈  
 現在您可以從您的範本建立專案，並使用自訂的精靈。  
  
1.  重建方案，並開始偵錯。 Visual Studio 的第二個執行個體應該會出現。  
  
2.  建立新的 MyProjectTemplate 專案。 (**檔案 / 新增 / 專案 / Visual C# / MyProjectTemplate**)  
  
3.  在 **新的專案** 對話方塊中，找出您的範本、 輸入名稱，並按一下 **確定**。  
  
     精靈的使用者輸入的表單隨即開啟。  
  
4.  輸入自訂參數的值，然後按一下  按鈕。  
  
     在精靈的使用者輸入的表單關閉，並從範本建立專案。  
  
5.  在 **方案總管**，以滑鼠右鍵按一下原始程式碼檔，然後按一下**檢視程式碼**。  
  
     請注意，`$custommessage$`已取代為精靈的使用者輸入表單中輸入的文字。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>   
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [WizardExtension 元素 (Visual Studio 範本)](../extensibility/wizardextension-element-visual-studio-templates.md)