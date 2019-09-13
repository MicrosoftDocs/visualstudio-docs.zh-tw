---
title: HOW TO：搭配專案範本使用精靈
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51c89fb82985d37b106f352047bfce74503f3c48
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913108"
---
# <a name="how-to-use-wizards-with-project-templates"></a>作法：搭配專案範本使用嚮導

Visual Studio 提供的<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>介面，在執行時，可讓您在使用者從範本建立專案時，執行自訂程式碼。

專案範本自訂可以用來顯示自訂 UI，以收集使用者輸入以自訂範本、將其他檔案加入至範本，或專案上允許的任何其他動作。

當使用者在 [**新增專案**] 對話方塊中按一下 **[確定]** 時，就會在建立專案時，在不同的時間呼叫介面方法。<xref:Microsoft.VisualStudio.TemplateWizard.IWizard> 介面的每個方法都會命名為，以描述呼叫它的時間點。 例如，Visual Studio 在開始<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>建立專案時立即呼叫，使其成為撰寫自訂程式碼以收集使用者輸入的好位置。

## <a name="create-a-project-template-project-with-a-vsix-project"></a>使用 VSIX 專案建立專案範本專案

您開始使用專案範本專案建立自訂範本，這是 Visual Studio SDK 的一部分。 在此程式中，我們將使用C#專案範本專案，但也有一個 Visual Basic 專案範本專案。 然後，將 VSIX 專案新增至包含專案範本專案的方案。

1. C#建立專案範本專案（在 Visual Studio 中 **，選取** > [檔案] [**新增** > ] **[專案]，然後搜尋**「專案範本」）。 將它命名為**MyProjectTemplate**。

   > [!NOTE]
   > 系統可能會要求您安裝 Visual Studio SDK。 如需詳細資訊，請參閱[安裝 VISUAL STUDIO SDK](../extensibility/installing-the-visual-studio-sdk.md)。

2. 在與專案範本專案相同的方案中加入新的 VSIX 專案（在**方案總管**中 **，選取方案** > 節點，按一下滑鼠右鍵，然後選取 [**新增專案**] 並搜尋 "VSIX"）。 將它命名為**MyProjectWizard。**

3. 將 VSIX 專案設定為啟始專案。 在**方案總管**中，選取 VSIX 專案節點，按一下滑鼠右鍵，然後選取 [**設定為啟始專案**]。

4. 將範本專案新增為 VSIX 專案的資產。 在**方案總管**的 VSIX 專案節點底下，尋找*extension.vsixmanifest*檔案。 按兩下它，在資訊清單編輯器中開啟它。

5. 在資訊清單編輯器中，選取視窗左側的 [**資產**] 索引標籤。

6. 在 [**資產**] 索引標籤中，選取 [**新增**]。 在 [**加入新資產**] 視窗的 [類型] 欄位中，選取 [ **VisualStudio ProjectTemplate**]。 在 [**來源**] 欄位中，選取 [**目前方案] 中的專案**。 在 [**專案**] 欄位中，選取 [ **MyProjectTemplate**]。 然後按一下 [確定]。

7. 建置方案並開始偵錯。 Visual Studio 的第二個執行個體隨即出現。 （這可能需要幾分鐘的時間）。

8. 在 Visual Studio 的第二個實例中，嘗試使用新的**範本（**  > [檔案] [**新增** > ] [**專案**]，搜尋 "myproject"）來建立新的專案。 新的專案應該會與名為**Class1**的類別一起出現。 您現在已建立自訂專案範本！ 立即停止調試。

## <a name="create-a-custom-template-wizard"></a>建立自訂範本 wizard

此程式示範如何建立自訂的 wizard，以在建立專案之前開啟 Windows Form。 表單可讓使用者新增在專案建立期間新增至原始程式碼的自訂參數值。

1. 設定 VSIX 專案，以允許它建立元件。

2. 在 **方案總管**中，選取 VSIX 專案 節點。 在下方**方案總管**，您應該會看到 [**屬性**] 視窗。 如果沒有，請選取 [**視圖** > **屬性視窗]** ，或按**F4**。 在 [**屬性**] 視窗中，選取下欄欄位`true`以：

   - **在 VSIX 容器中包含元件**

   - **在 VSIX 容器中包含 Debug 符號**

   - **在本機 VSIX 部署中包含 Debug 符號**

3. 將元件當做資產新增至 VSIX 專案。 開啟*extension.vsixmanifest*檔案，然後選取 [**資產**] 索引標籤。在 [**加入新資產**] 視窗中，針對 [**類型**] 選取 [ **VisualStudio**]，針對 [**來源**] 選取 [**目前方案中的專案**]，然後針對 [**專案**] 選取 [ **MyProjectWizard**]。

4. 將下列參考加入至 VSIX 專案。 （在**方案總管**的 VSIX 專案節點底下，選取 [**參考**]，以滑鼠右鍵按一下，然後選取 [**新增參考**]。）在 [**加入參考**] 對話方塊的 [**架構**] 索引標籤中，尋找 [system.object]，然後選取 [ **Windows Forms** ] 元件。 另請尋找並選取 [**系統**] 和 [ **system. 繪圖**] 元件。 現在選取 [**延伸**模組] 索引標籤。尋找**EnvDTE**元件並加以選取。 另請尋找**TemplateWizardInterface**元件並加以選取。 按一下 [確定 **Deploying Office Solutions**]。

5. 將 wizard 執行的類別加入至 VSIX 專案。 （在**方案總管**中，以滑鼠右鍵按一下 VSIX 專案節點，然後依序選取 [**加入**]、[**新增專案**] 和 [**類別**]）。將類別命名為**WizardImplementation**。

6. 將*WizardImplementationClass.cs*檔案中的程式碼取代為下列程式碼：

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

    稍後將會執行此程式碼中所參考的**UserInputForm** 。

    類別包含每個成員的<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>方法執行。 `WizardImplementation` 在此範例中，只有<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>方法會執行工作。 所有其他方法都不會執行任何`true`動作，也不會傳回。

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>方法接受四個參數：

   - 可以轉換成根<xref:EnvDTE._DTE>物件的參數，可讓您自訂專案。<xref:System.Object>

   - <xref:System.Collections.Generic.Dictionary%602>參數，其中包含範本中所有預先定義之參數的集合。 如需範本參數的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>參數，其中包含所使用之範本類型的相關資訊。

   - <xref:System.Object>陣列，其中包含由 Visual Studio 傳遞至 wizard 的一組參數。

     這個範例會將使用者輸入表單中的參數值新增<xref:System.Collections.Generic.Dictionary%602>至參數。 專案中`$custommessage$`參數的每個實例都會取代為使用者輸入的文字。

7. 現在，請建立**UserInputForm**。 在*WizardImplementation.cs*檔案中，將下列程式碼新增至`WizardImplementation`類別的結尾之後。

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
               this.Close();
           }
       }
   ```

    使用者輸入表單提供簡單的表單來輸入自訂參數。 表單包含名為`textBox1`的文字方塊和名為`button1`的按鈕。 按一下按鈕時，文字方塊中的文字會儲存在`customMessage`參數中。

## <a name="connect-the-wizard-to-the-custom-template"></a>將嚮導連接到自訂範本

為了讓您的自訂專案範本使用您的自訂嚮導，您需要簽署 wizard 元件，並在自訂專案範本中加入一些行，讓它知道建立新專案時，要在何處找到 wizard 的執行。

1. 簽署元件。 在 **方案總管**中，選取 VSIX 專案，按一下滑鼠右鍵，然後選取 **專案屬性**。

2. 在 [**專案屬性**] 視窗中，選取 [**簽署**] 索引標籤。在 [**簽署**] 索引標籤中，勾選 [**簽署元件**]。 在 **選擇強式名稱金鑰檔**欄位中，選取 **\<新增>** 。 在 [**建立強式名稱金鑰**] 視窗，請在**金鑰檔名稱**欄位中，輸入 **key.snk** 。 取消核取 [**使用密碼保護我的金鑰**檔] 欄位。

3. 在 **方案總管**中，選取 VSIX 專案並尋找 **屬性** 視窗。

4. 將 [**將組建輸出複製到輸出目錄**] 欄位設定為 [ **true**]。 這可在重建方案時，將元件複製到輸出目錄中。 它仍然包含在檔案中`.vsix` 。 您必須查看元件，才能找出其簽署金鑰。

5. 重建方案。

6. 您現在可以在 MyProjectWizard 專案目錄（ *\<您的磁片位置 > \MyProjectTemplate\MyProjectWizard\key.snk*）中找到金鑰 .snk 檔案。 複製*金鑰 .snk*檔案。

7. 移至輸出目錄，並尋找元件（ *\<您的磁片位置 > \ MyProjectTemplate/MyProjectWizard \ bin \ Debug \ MyProjectWizard .dll*）。 在這裡貼上*金鑰 .snk*檔案。 （這並非絕對必要，但可讓下列步驟更容易）。

8. 開啟命令視窗，並變更至已建立元件的目錄。

9. 尋找*sn.exe*簽署工具。 例如，在 Windows 10 64 位的作業系統上，典型的路徑如下所示：

     *C:\Program Files (x86)\Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     如果您找不到此工具，請嘗試在命令視窗中執行**其中的/r. sn.exe** 。 記下路徑。

10. 從*金鑰 .snk*檔案解壓縮公開金鑰。 在命令視窗中，輸入

     **\<sn.exe 的位置 > \sn.exe-p key .snk outfile 機碼。**

     如果目錄名稱中有空格，別忘了用引號括住*sn.exe*的路徑！

11. 從 outfile 取得公開金鑰 token：

     **\<sn.exe 的位置 > \sn.exe-t outfile. key。**

     同樣地，別忘了加上引號。 您應該會在輸出中看到一行，如下所示

     **公開金鑰 token 是\<token >**

     記下此值。

12. 將自訂嚮導的參考新增至專案範本的 *.vstemplate*檔案。 在 **方案總管**中，尋找名為*MyProjectTemplate*的檔案，然後將它開啟。 在\<TemplateContent > 區段結尾之後，新增下列區段：

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     其中**MyProjectWizard**是元件的名稱，而**token**則是您在上一個步驟中複製的權杖。

13. 儲存專案中的所有檔案，並重建。

## <a name="add-the-custom-parameter-to-the-template"></a>將自訂參數新增至範本

在此範例中，做為範本使用的專案會顯示在自訂嚮導的使用者輸入表單中指定的訊息。

1. 在**方案總管**中，移至**MyProjectTemplate**專案，然後開啟*Class1.cs*。

2. 在應用程式的方法中，加入下列程式程式碼。`Main`

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    從範本`$custommessage$`建立專案時，會將參數取代為使用者輸入表單中輸入的文字。

以下是完整的程式碼檔案，然後再將其匯出至範本。

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

## <a name="use-the-custom-wizard"></a>使用自訂嚮導

現在您可以從範本建立專案，並使用自訂嚮導。

1. 重建方案並開始進行調試。 Visual Studio 的第二個執行個體應該會出現。

2. 建立新的 MyProjectTemplate 專案。  >  （[檔案][新增專案]）。 > 

3. 在 [**新增專案**] 對話方塊中，搜尋 "myproject" 以找出您的範本、輸入名稱，然後按一下 **[確定]** 。

     Wizard 使用者輸入表單隨即開啟。

4. 輸入自訂參數的值，然後按一下按鈕。

     Wizard 使用者輸入表單隨即關閉，並從範本建立專案。

5. 在**方案總管**中，以滑鼠右鍵按一下原始程式碼檔案，然後按一下 [**查看程式碼**]。

     請注意`$custommessage$` ，已取代為在 wizard 使用者輸入表單中輸入的文字。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [WizardExtension 元素（Visual Studio 範本）](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Visual Studio 範本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)
