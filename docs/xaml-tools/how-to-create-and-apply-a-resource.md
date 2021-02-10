---
title: 如何建立和套用資源
description: 瞭解如何在 XAML 設計工具中建立和套用資源，以便您可以儲存和重複使用專案的樣式和範本。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6c6c243896370cc97b8a85d5de520c4c033d49b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971605"
---
# <a name="how-to-create-and-apply-a-resource"></a>如何建立和套用資源

XAML 設計工具中的項目樣式和樣板會儲存在可重複使用的實體中 (稱為資源)。 樣式可讓您設定項目屬性，並重複使用這些設定，以確保多個項目有一致的外觀。 [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) 可以定義控制項的外觀，也可以當作資源來套用。 如需詳細資訊，請參閱 [XAML 樣式](/windows/uwp/design/controls-and-patterns/xaml-styles)和[控制項範本](/windows/uwp/design/controls-and-patterns/control-templates)。

每當您從現有的屬性、[Style](xref:Windows.UI.Xaml.Style) 或 [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) 建立新資源時，[建立資源] 對話方塊都可讓您定義應用程式層級、文件層級或元素層級的資源。 這些層級會決定您可以使用資源的位置。 例如，如果您在項目層級定義資源，該資源只能套用至用來建立資源的項目。 您也可以選擇將資源儲存在[資源字典](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references)中；資源字典是您可以在其他專案中重複使用的個別檔案。

## <a name="create-a-new-resource"></a>建立新的資源

1. 在 XAML 設計工具中開啟 XAML 檔案後，建立一個項目，或在 [文件大綱] 視窗中選擇一個項目。

2. 在 [屬性] 視窗中，選擇屬性標記 (顯示為屬性值右邊的方塊符號)，然後選擇 [轉換成新資源]。 白色方塊符號表示預設值，而黑色方塊符號通常表示已套用本機資源。

     這會顯示用於建立資源的適當對話方塊。 例如，當您從筆刷建立資源時，會顯示下列對話方塊：

     ![[建立資源] 對話方塊](../designers/media/xaml_create_resource.png)

3. 在 [名稱 (索引鍵)] 方塊中，輸入索引鍵名稱。 如果您要讓其他項目參考這個資源，這會是您使用的名稱。

4. 在 [定義於] 底下，選擇指定要定義資源位置的選項：

    - 若要將資源提供給應用程式中的所有文件使用，請選擇 [應用程式]。

    - 若要將資源只提供給目前的文件使用，請選擇 [此文件]。

    - 若要將資源只提供給您用來建立資源的元素或其子元素使用，請選擇 [此文件]，然後從下拉式清單中選取 [元素: 名稱]。

    - 若要在可重複在其他專案中使用的[資源字典](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references)檔案中定義資源，請按一下 [資源字典]。 然後，在下拉式清單中選取現有的資源字典檔案 (例如 **StandardStyles.xaml**)。

5. 選擇 [確定] 按鈕來建立資源，然後將它套用至您用來建立資源的元素。

## <a name="apply-a-resource-to-an-element-or-property"></a>將資源套用至元素或屬性

1. 在 [文件大綱] 視窗中，選擇您要套用資源的項目。

2. 執行下列其中一個動作：

   - 將資源套用至屬性。 在 [ **屬性** ] 視窗中，選擇屬性值旁邊的屬性標記，選擇 [ **本機資源** ] 或 [ **系統資源**]，然後從顯示的清單中選擇可用的資源。

      如果您看不到預期應出現的資源，可能是因為資源類型不符合屬性類型。

   - 將樣式或控制項樣板資源套用至控制項。 開啟 [文件大綱] 視窗中控制項的右鍵功能表 (操作功能表)、選擇 [編輯範本] 或 [編輯其他範本]、選擇 [套用資源]，然後從出現的清單中選擇控制項範本的名稱。

     > [!NOTE]
     > [編輯範本] 會套用控制項範本。 [編輯其他範本] 會套用其他範本類型。

     只要資源相容，就可以套用資源。 例如，您可以將筆刷資源套用至 [TextBox](xref:Windows.UI.Xaml.Controls.TextBox) 控制項的 **Foreground** 屬性。

## <a name="edit-a-resource"></a>編輯資源

1. 在畫板上或在 [文件大綱] 視窗中選擇一個項目。

2. 選擇 [屬性] 視窗中位於該屬性右邊的 [預設] 或 [本機] 屬性標記，然後選擇 [編輯資源] 以開啟 [編輯資源] 對話方塊。

3. 修改資源的選項。

## <a name="see-also"></a>另請參閱

- [使用 XAML 設計工具建立 UI](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
