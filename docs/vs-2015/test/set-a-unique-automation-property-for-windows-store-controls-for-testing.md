---
title: 為用於測試的 Windows 市集控制項設定唯一自動化屬性 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6ce207776fe2f3dfe00ddc764546a370dbb53dca
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107031"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>為用於測試的 Windows 市集控制項設定唯一自動化屬性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

如果您想要執行 XAML Windows 市集應用程式的自動程式碼 UI 測試，則必須具有可識別每個控制項的唯一自動化屬性。  
  
 您可以根據應用程式中的 XAML 控制項類型來指派唯一自動化屬性。 以下是在下列情況中指派這個唯一自動化屬性的方法︰  
  
- [控制項的靜態 XAML 定義](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
- [使用 Visual Studio 或 Blend for Visual Studio 指派唯一自動化屬性](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
- [使用 DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
- [使用控制項範本](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
- [動態控制項](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## <a name="use-methods-to-assign-a-unique-automation-property"></a>使用方法來指派唯一自動化屬性  
  
### <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> 靜態 XAML 定義  
 若要指定 XAML 檔案中所定義之控制項的唯一自動化屬性，您可以隱含或明確地設定 AutomationProperties.AutomationId 或 AutomationProperties.Name，如下列範例所示。 設定任一值會提供控制項的唯一自動化屬性，以用來在建立自動程式碼 UI 測試或動作記錄時識別控制項。  
  
 **隱含地設定屬性**  
  
 在 XAML 中，使用 Name 屬性，將控制項的 AutomationProperties.AutomationId 設定為 **ButtonX**。  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 在 XAML 中，使用 Content 屬性，將控制項的 AutomationProperties.Name 設定為 **ButtonY**。  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **明確地設定屬性**  
  
 在 XAML 中，將控制項的 AutomationProperties.AutomationId 明確地設定為 **ButtonX**。  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 在 XAML 中，將控制項的 AutomationProperties.Name 明確地設定為 **ButtonY**。  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
### <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> 使用 Visual Studio 或 Blend for Visual Studio 指派唯一自動化屬性  
 您可以使用 Visual Studio 或 Blend for Visual Studio 將唯一名稱指派給互動項目，例如按鈕、清單方塊、下拉式方塊和文字方塊。 這裡提供控制項之 AutomationProperties.Name 的唯一值。  
  
 **Visual Studio 中：** 在 [工具]  功能表上，指向 [選項]  ，然後依序選擇 [文字編輯器] 、[XAML] 和 [其他] 。  
  
 選取 [建立時自動命名互動項目]，然後選擇 [確定]。  
  
 ![XAML 其他選項](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
 **Blend for Visual Studio:** 您可以使用下列方法之一來從 Blend for Visual Studio 執行此動作。  
  
> [!NOTE]
>  針對使用 XAML 靜態建立的控制項，您只能使用這個方法。  
  
 **提供現有控制項的唯一名稱**  
  
 在 [工具] 功能表上，選擇 [命名互動項目]，如下所示：  
  
 ![從 [工具] 功能表選擇 [命名互動項目]](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")  
  
 **自動提供所建立控制項的唯一名稱**  
  
 在 [工具] 功能表上，指向 [選項]，然後選擇 [專案]。 選取 [建立時自動命名互動項目]，然後選擇 [確定]，如下所示：  
  
 ![設定專案以命名互動項目](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")  
  
### <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> 使用資料範本  
 您可以使用下列 XAML 定義使用 ItemTemplate 的簡單範本，以將清單方塊中的值繫結至變數。  
  
```xaml  
  
<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
   <ListBox.ItemTemplate>  
      <DataTemplate>  
         <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding EmployeeName}" />  
            <TextBlock Text="{Binding EmployeeID}" />  
         </StackPanel>  
      </DataTemplate>  
   </ListBox.ItemTemplate>  
</ListBox>  
```  
  
 您也可以使用下列 XAML 使用具有 ItemContainerStyle 的範本，以將值繫結至變數。  
  
```xaml  
  
      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">  
            <ListBox.ItemContainerStyle>  
                <Style TargetType="ListBoxItem">  
                    <Setter Property="Template">  
                        <Setter.Value>  
                            <ControlTemplate TargetType="ListBoxItem">  
                                <Grid>  
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>  
                                </Grid>  
                            </ControlTemplate>  
                        </Setter.Value>  
                    </Setter>  
                </Style>  
            </ListBox.ItemContainerStyle>           
        </ListBox>  
  
```  
  
 針對這兩個範例，您必須接著覆寫 ItemSource 的 ToString() 方法，如使用下列程式碼所示。 此程式碼可確保 AutomationProperties.Name 值已設定而且是唯一的，因為您無法使用繫結來設定每個資料繫結清單項目的唯一自動化屬性。 在此情況下，設定 AutomationProperties.Name 的唯一值就已足夠。  
  
> [!NOTE]
>  使用這個方法，也可以透過繫結，將清單項目的內部內容設定為「員工」類別中的字串。 如本範例所示，每個清單項目內的按鈕控制項都會獲指派本身為員工識別碼的唯一自動化識別碼。  
  
```  
  
Employee[] employees = new Employee[]   
{  
   new Employee("john", "4384"),  
   new Employee("margaret", "7556"),  
   new Employee("richard", "8688"),  
   new Employee("george", "1293")  
};  
  
listBox1.ItemsSource = employees;  
  
public override string ToString()  
{  
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name  
}  
  
```  
  
### <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> 使用控制項範本  
 您可以使用控制項範本，讓特定類型的每個執行個體取得在程式碼中所定義的唯一自動化屬性。 您必須建立範本，以讓 AutomationProperty 繫結至控制項執行個體中的唯一識別碼。 下列 XAML 示範如何使用控制項範本建立此繫結的一種方法。  
  
```xaml  
  
<Style x:Key="MyButton" TargetType="Button">  
<Setter Property="Template">  
   <Setter.Value>  
<ControlTemplate TargetType="Button">  
   <Grid>  
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>  
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>  
   </Grid>  
</ControlTemplate>  
   </Setter.Value>  
</Setter>  
</Style>  
  
```  
  
 當您使用此控制項範本定義按鈕的兩個執行個體時，自動化識別碼會設定為範本中控制項的唯一內容字串，如下列 XAML 所示。  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
### <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> 動態控制項  
 如果您的控制項是從程式碼動態建立，而不是靜態建立或透過 XAML 檔案中的範本建立，則必須設定控制項的 Content 或 Name 屬性。 如此可確保每個動態控制項都具有唯一自動化屬性。 例如，如果您有必須在選取清單項目時顯示的核取方塊，則可以設定這些屬性，如下所示︰  
  
```csharp  
  
private void CreateCheckBox(string txt, StackPanel panel)  
   {  
      CheckBox cb = new CheckBox();  
      cb.Content = txt; // Sets the AutomationProperties.Name  
      cb.Height = 50;  
      cb.Width = 100;  
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId  
      panel.Children.Add(cb);  
    }  
  
```  
