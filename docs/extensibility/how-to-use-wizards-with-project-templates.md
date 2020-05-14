---
title: 如何：搭配專案範本使用精靈
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d2dc057dfa518bb52c6ba4d30cd0f3e0a822cfd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710538"
---
# <a name="how-to-use-wizards-with-project-templates"></a>如何:將精靈與專案樣本一起使用

Visual Studio<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>提供了該介面,當實現該介面時,用戶可以在用戶從範本創建專案時運行自定義代碼。

專案範本自定義可用於顯示自訂 UI,用於收集使用者輸入以自訂樣本、向範本添加其他檔或專案上允許的任何其他操作。

在<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>創建專案時,在不同時間調用介面方法,從使用者單擊 **「新項目**」對話方塊上的 **「確定」** 開始。 命名介面的每個方法來描述調用它的點。 例如,Visual Studio<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>在開始創建專案時立即調用,使其成為編寫自訂代碼以收集使用者輸入的良好位置。

## <a name="create-a-project-template-project-with-a-vsix-project"></a>使用 VSIX 專案建立項目樣本專案

開始使用專案範本項目創建自定義範本,該專案是可視化工作室 SDK 的一部分。 在此過程中,我們將使用 C# 專案樣本專案,但也有 Visual Basic 專案樣本專案。 然後,將 VSIX 專案添加到包含專案範本專案的解決方案。

1. 創建 C# 專案樣本專案(在視覺化工作室中,選擇 **「檔** > **新專案** > **」並**搜尋「專案範本」)。 將其命名為 **「我的項目範本**」 。

   > [!NOTE]
   > 系統可能會要求您安裝可視化工作室 SDK。 有關詳細資訊,請參閱[安裝可視化工作室 SDK](../extensibility/installing-the-visual-studio-sdk.md)。

2. 在專案範本專案相同的解決方案中添加新的 VSIX 專案(在**解決方案資源管理器**中,選擇解決方案節點,右鍵單擊,然後選擇 **「添加新** > **專案**」並搜尋「vsix」)。 將其命名為 **「我的項目嚮導」。**

3. 將 VSIX 專案設置為啟動專案。 在**解決方案資源管理器**中,選擇 VSIX 專案節點,右鍵單擊,然後選擇「**設定為啟動專案**」 。。

4. 將範本專案添加為 VSIX 專案的資產。 在**解決方案資源管理員**中,在 VSIX 專案節點下,尋找*來源.擴展.vsixmanifest*檔案。 按兩下它以在清單編輯器中打開它。

5. 在清單編輯器中,選擇視窗左側的「**資產**」選項卡。

6. 在「**資產**」選項卡中,選擇 **「新建**」。。 在「**新增新資產**」 視窗中,對於「類型」欄位,選擇**Microsoft.VisualStudio.ProjectTemplate**。 在 **「來源」** 欄位中,選擇**目前解決方案中的項目**。 在 **「專案」** 欄位中,選擇 **「我的項目範本**」 。。 然後按一下 **[確定]**。

7. 建置方案並開始偵錯。 Visual Studio 的第二個執行個體隨即出現。 (這可能需要數分鐘的時間)。

8. 在 Visual Studio 的第二個實例中,嘗試使用新範本創建新**專案**(**檔** > **新專案** > ,搜索"我的專案")。 新專案應與名為**Class1**的類一起出現。 您現在已創建自定義項目範本! 現在停止調試。

## <a name="create-a-custom-template-wizard"></a>建立自訂樣本精靈

此過程展示如何建立在創建專案之前打開 Windows 窗體的自訂嚮導。 該表單單允許使用者新增在專案創建期間添加到原始碼的自訂參數值。

1. 設置 VSIX 專案以允許它創建程式集。

2. 在**解決方案資源管理器中**,選擇 VSIX 專案節點。 在**解決方案資源管理員**下方 ,應看到 **"屬性"** 視窗。 否則,請選擇 **「查看** > **」 屬性視窗**「 或按**F4**。 在 **「屬性」** 視窗中, 選擇以下`true`欄位以 :

   - **在 VSIX 容器中包括程式集**

   - **在 VSIX 容器中包含除錯符號**

   - **在本地 VSIX 部署中包含除錯符號**

3. 將程式集作為資產添加到 VSIX 專案中。 開啟*來源.擴展.vsixmanifest*檔案並選擇「**資產**」選項卡。在 **「新增新資產**」視窗中,對於**類型**,請選擇**Microsoft.VisualStudio.Assembly,** 對於**來源**選擇**當前解決方案中的專案**,並且對於**項目**選擇 **「我的專案向導**」。

4. 添加以下對 VSIX 專案的引用。 (在 **"解決方案資源管理器**"中,在 VSIX 專案節點下,選擇 **"引用**",右鍵單擊,然後選擇 **"添加參考**"。"在「**添加參考**」對話方塊中,在 **「框架」** 選項卡中,尋找**System.Windows 窗體**程式集並選擇它。 還要查找並選擇**系統和****系統.繪圖**程式集。 現在選擇 **「擴展」** 選項卡。找到**EnvDTE**程式集並選擇它。 還可以找到**Microsoft.VisualStudio.範本嚮導介面**程式集並選擇它。 按一下 [確定]  。

5. 向 VSIX 專案添加嚮導實現的類。 ( 在**解決方案資源管理員**中, 右鍵按下 VSIX 專案節點,然後選擇 **'新增**',然後選擇 **'新增專案**",然後選擇**類別**。)命名類別**精靈 。**

6. 將*WizardImplementationClass.cs*檔案中的代碼取代為以下代碼:

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

    此代碼中引用**的用戶輸入形式**將在以後實現。

    該`WizardImplementation`類<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>包含的每個成員的方法實現。 在此示例中,只有方法<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>執行任務。 所有其他方法要麼不執行任何操作,`true`要麼傳回 。

    該方法<xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>接受四個參數:

   - 可以<xref:System.Object>強制轉換為根<xref:EnvDTE._DTE>物件的參數,以便自定義專案。

   - 包含<xref:System.Collections.Generic.Dictionary%602>樣本中所有預定義參數的集合的參數。 有關樣本參數的詳細資訊,請參閱[樣本參數](../ide/template-parameters.md)。

   - 包含有關<xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>正在使用哪種範本的參數。

   - 包含<xref:System.Object>由 Visual Studio 傳遞給嚮導的一組參數的陣列。

     本示例將使用者輸入表單中的參數值添加到參數。 <xref:System.Collections.Generic.Dictionary%602> 項目中`$custommessage$`參數的每個實體都將替換為使用者輸入的文本。

7. 現在建立**使用者輸入表單**。 在*WizardImplementation.cs*檔中,在`WizardImplementation`類結束后添加以下代碼。

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

    使用者輸入表單提供用於輸入自訂參數的簡單窗體。 該表單包含一個名稱為`textBox1`的文字框和名為`button1`的按鈕。 點選按鈕時,文字框中的文字會儲存在 參數`customMessage`中 。

## <a name="connect-the-wizard-to-the-custom-template"></a>將精靈連線到自訂樣本

為了使自定義專案範本使用自定義嚮導,您需要對嚮導程式集進行簽名,並將一些行添加到自定義專案範本中,以便知道在創建新專案時在哪裡可以找到嚮導實現。

1. 對程式集進行簽名。 在**解決方案資源管理器**中,選擇 VSIX 專案,右鍵單擊,然後選擇 **「專案屬性**」。

2. 在「**項目屬性**」視窗中,在 **「簽名**」選項卡中選擇「**簽名**」選項卡,選擇 **「對程式集進行簽名**」 。 在**選擇強名稱鍵檔欄位中**,選擇**\<「新>」。。 ** 在 **'建立強名稱鍵'** 視窗中,在 **「鍵檔名**」欄位中,鍵入**key.snk**。 使用密碼欄位取消選選擇 **「保護我的密鑰檔**」。

3. 在**解決方案資源管理員**中,選擇 VSIX 專案並找到 **「屬性」** 視窗。

4. 將 **'將產生輸出複製到輸出目錄'** 欄位設定為**true**。 這允許在重建解決方案時將程式集複製到輸出目錄中。 它仍然包含在`.vsix`檔中。 您需要查看程式集,以便找出其簽名金鑰。

5. 重建方案。

6. 您現在可以在 MyProjectWizard 專案目錄中找到 key.snk 檔(*\<您的磁碟位置>_MyProjectTemplate_MyProjectWizard_key.snk)。* 複製*金鑰.snk*檔。

7. 跳到輸出目錄並找到程式集(*\<您的磁碟位置>_MyProjectTemplate/MyProjectWizard_bin_Debug_MyProjectWizard.dll)。* 在此處粘貼*金鑰.snk*檔。 (這不是絕對必要的,但它將使以下步驟更容易。

8. 開啟命令視窗,並更改為在其中創建程式集的目錄。

9. 尋找*sn.exe*簽名工具。 例如,在 Windows 10 64 位元作業系統上,典型的路徑如下:

     *C:\程式檔 (x86)\微軟 SDK\Windows\v10.0A\bin_NETFX 4.6.1 工具*

     如果找不到此工具,請嘗試在指令視窗中執行 **/R . sn.exe 的位置**。 記下路徑。

10. 從*key.snk*檔中提取公開金鑰。 在命令視窗中鍵入

     **\<sn.exe>\sn.exe-p 鍵.snk outfile.key 的位置。**

     如果目錄名稱中有空格,不要忘記用引號環繞*sn.exe*的路徑!

11. 從外檔案取得公開金鑰權杖:

     **\<sn.exe>\sn.exe-t outfile.key 的位置。**

     再次,不要忘記引號。 您應該在輸出中看到以下所示的行

     **公開金鑰權杖\<是 權杖>**

     記下此值。

12. 將對自定義精靈的引用添加到專案範本的 *.vstemplate*檔中。 在**解決方案資源管理員**中,找到名為*MyProjectTemplate.vstemplate*的檔案,然後打開它。 \<在「範本內容>」部分結束後,添加以下部分:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     **其中 MyProjectWizard**是程式集的名稱,**令牌**是您在上一步複製的權杖。

13. 保存專案中的所有檔並重新生成。

## <a name="add-the-custom-parameter-to-the-template"></a>將自訂參數加入樣本

在此範例中,用作範本的項目顯示在自定義嚮導的使用者輸入窗體中指定的消息。

1. 在**解決方案資源管理員**中,轉到**MyProjectTemplate**專案並開啟*Class1.cs*。

2. 在`Main`應用程式的方法中,添加以下代碼行。

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    當從`$custommessage$`樣本創建專案時,參數將替換為在使用者輸入窗體中輸入的文本。

下面是完整代碼檔,在該檔已匯出到範本之前。

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

## <a name="use-the-custom-wizard"></a>使用自訂精靈

現在,您可以使用範本創建專案並使用自定義嚮導。

1. 重建解決方案並開始調試。 Visual Studio 的第二個執行個體應該會出現。

2. 創建新的 MyProjectTemplate 專案。 (**檔案** > **新專案** > **Project**)。

3. 在 **「新項目**」對話框中,搜索「我的專案」以查找範本、鍵入名稱,然後單擊「**確定**」。

     嚮導使用者輸入窗體將打開。

4. 鍵入自定義參數的值,然後單擊該按鈕。

     嚮導使用者輸入窗體將關閉,並且從範本創建專案。

5. 在**解決方案資源管理器**中,右鍵單擊原始程式碼檔,然後單擊 **「查看代碼**」。。

     `$custommessage$`已替換為嚮導使用者輸入表單中輸入的文字的通知。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [自訂範本](../ide/customizing-project-and-item-templates.md)
- [嚮導延伸元素(可視化工作室範本)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [視覺工作室樣本中的 NuGet 套件](/nuget/visual-studio-extensibility/visual-studio-templates)
