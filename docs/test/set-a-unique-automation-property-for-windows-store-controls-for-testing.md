---
title: 設定獨特的自動化屬性-測試 UWP 控制項
description: 瞭解如何在以 XAML 為基礎的 UWP 應用程式中，根據 XAML 控制項的類型來指派唯一自動化屬性，以執行自動程式碼 UI 測試。
ms.custom: SEO-VS-2020
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 1befcb77e0ade11a9a3be51a2750564fd316efcd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884490"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>為 UWP 控制項設定唯一自動化屬性以進行測試

如果您想要執行以 XAML 為基礎之 UWP 應用程式的自動程式化 UI 測試，則必須以唯一的自動化屬性識別每個控制項。 您可以根據應用程式中的 XAML 控制項類型來指派唯一自動化屬性。

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>靜態 XAML 定義

若要為 XAML 檔案中定義的控制項指定唯一 automation 屬性，您可以隱含或明確地設定 **AutomationProperties AutomationId** 或 **AutomationProperties.Name** ，如下列範例所示。 設定任一值會提供控制項的唯一自動化屬性，以用來在建立自動程式碼 UI 測試或動作記錄時識別控制項。

### <a name="set-the-property-implicitly"></a>隱含設定屬性

在 XAML 中，使用 **Name** 屬性，將控制項的 **AutomationProperties.AutomationId** 設定為 **ButtonX**。

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

在 XAML 中，使用 **Content** 屬性，將控制項的 **AutomationProperties.Name** 設定為 **ButtonY**。

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>明確地設定屬性

在 XAML 中，將控制項的 **AutomationProperties.AutomationId** 明確地設定為 **ButtonX**。

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

在 XAML 中，將控制項的 **AutomationProperties.Name** 明確設定為 **ButtonY**。

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>指派唯一的名稱

在 Blend for Visual Studio 中，您可以選取選項，將唯一名稱指派給互動式項目，例如按鈕、清單方塊、下拉式方塊和文字方塊，這讓控制項具有 **AutomationProperties.Name** 的唯一值。

若要將唯一名稱指派給現有的控制項，請選取 [**工具**  >  **名稱互動元素**]。

![在 Blend for Visual Studio 中命名互動式元素](../test/media/cuit_windowsstoreproperty_blend_1.png)

若要自動將唯一名稱提供給您新增的新控制項，請選取 [**工具**  >  **選項**] 以開啟 [**選項**] 對話方塊。 選取 [XAML 設計工具]，然後選取 [建立時自動命名互動式元素]。 選取 [確定] 關閉對話方塊。

## <a name="use-a-data-template"></a>使用資料範本

您可以使用 **ItemTemplate** 來定義簡單範本，以將清單方塊中的值繫結至變數：

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

您也可以使用範本搭配 **ItemContainerStyle**，以將值繫結至變數：

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

針對這兩個範例，您必須接著覆寫 **ItemSource** 的 **ToString()** 方法，如使用下列程式碼範例所示。 此程式碼可確保 **AutomationProperties.Name** 值已設定而且是唯一的，因為您無法使用繫結來設定每個資料繫結清單項目的唯一自動化屬性。 在此情況下，設定 **AutomationProperties.Name** 的唯一值就已足夠。

> [!NOTE]
> 使用這個方法，也可以透過繫結，將清單項目的內部內容設定為「員工」類別中的字串。 如本範例所示，每個清單項目內的按鈕控制項都會獲指派本身為員工識別碼的唯一自動化識別碼。

```csharp
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

## <a name="use-a-control-template"></a>使用控制項範本

您可以使用控制項範本，讓特定類型的每個執行個體取得在程式碼中所定義的唯一自動化屬性。 請建立範本，以讓 **AutomationProperty** 繫結至控制項執行個體中的唯一識別碼。 下列 XAML 示範如何使用控制項範本建立此繫結的一種方法：

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

當您使用此控制項範本定義按鈕的兩個執行個體時，自動化識別碼會設定為範本中控制項的唯一內容字串，如下列 XAML 所示：

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>動態控制項

如果您的控制項是從程式碼動態建立，而不是靜態建立或透過 XAML 檔案中的範本建立，則必須設定控制項的 **Content** 或 **Name** 屬性。 此動作可確保每個動態控制項都具有唯一自動化屬性。 例如，如果您有必須在選取清單項目時顯示的核取方塊，則可以設定這些屬性，如下所示︰

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

## <a name="see-also"></a>另請參閱

- [使用自動程式碼 UI 測試來測試 UWP 應用程式](../test/test-uwp-app-with-coded-ui-test.md)
