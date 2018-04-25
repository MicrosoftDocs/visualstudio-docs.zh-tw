---
title: 如何： 存取的內建的字型和色彩配置 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f72640369152b03ef86383fda1162b1cfbacba8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>如何： 存取的內建的字型和色彩配置
Visual Studio 整合式的開發環境 (IDE) 將其 [編輯器] 視窗相關聯字型和色彩的配置。 您可以存取透過此配置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。

 若要使用的內建的字型和色彩配置，VSPackage 必須：

-   定義要使用的預設字型和色彩的服務類別。

-   預設字型和色彩伺服器註冊類別。

-   建議特定的視窗藉由使用內建的顯示項目和類別目錄使用 IDE<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer>介面。

 IDE 使用產生的類別目錄做為視窗的控制代碼。 類別目錄的名稱會顯示在**顯示設定：**下拉式清單方塊中的**字型和色彩**屬性頁。

### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>若要定義類別，使用內建的字型和色彩

1.  建立任意的 GUID。

     此 GUID 用來唯一識別類別**。** IDE 的預設字型和色彩規格，會重複使用此類別。

    > [!NOTE]
    >  字型和色彩以擷取資料時<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>或其他介面，Vspackage 會使用此 GUID 參考內建的資訊。

2.  類別目錄的名稱必須加入 VSPackage 的資源 (.rc) 檔，請在字串資料表，使它可以視需要在 IDE 中顯示時當地語系化。

     如需詳細資訊，請參閱[加入或刪除字串](/cpp/windows/adding-or-deleting-a-string)。

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>若要註冊分類，使用內建的字型和色彩

1.  建構一種特殊類型的類別目錄中的下列位置的登錄項目：

     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version>* \FontAndColors\\*\<Category>*]

     *\<類別目錄 >* 為非當地語系化的類別目錄名稱。

2.  填入登錄以便使用內建字型和色彩配置具有四個值：

    |名稱|類型|資料|描述|
    |----------|----------|----------|-----------------|
    |分類|REG_SZ|GUID|任意的 GUID，識別包含內建的字型和色彩配置的分類。|
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> 此 GUID 可供使用的預設字型和色彩設定的所有 Vspackage。|
    |NameID|REG_DWORD|識別碼|在 VSPackage 中的可當地語系化的類別目錄名稱的資源識別碼。|
    |ToolWindowPackage|REG_SZ|GUID|VSPackage 實作的 GUID<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>若要起始使用系統提供的字型和色彩

1.  建立的執行個體<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>介面視窗的實作和初始化的過程。

2.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法，以取得執行個體<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer>介面對應至目前<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>執行個體。

3.  呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>兩次。

    -   以一次呼叫`VSEDITPROPID_ViewGeneral_ColorCategory`做為引數。

    -   以一次呼叫`VSEDITPROPID_ViewGeneral_FontCategory`做為引數。

     此設定，並公開為屬性 視窗的預設字型和色彩服務。

## <a name="example"></a>範例
 下列範例會起始使用內建的字型和色彩。

```cpp
CComVariant vt;
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);
if (spPropCatContainer != NULL){
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,
                                                          &spPropContainer))){
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);
    }
}
```

## <a name="see-also"></a>另請參閱

- [使用字型和色彩](../extensibility/using-fonts-and-colors.md)
- [取得字型和色彩資訊文字的顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)
- [字型和色彩概觀](../extensibility/font-and-color-overview.md)