---
title: HOW TO：存取的內建的字型和色彩配置 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685313"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>HOW TO：存取的內建的字型和色彩配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 整合式的開發環境 (IDE) 有 [編輯器] 視窗相關聯的字型和色彩配置。 您可以透過此配置<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。  
  
 若要使用的內建的字型和色彩配置，VSPackage 必須：  
  
- 定義要使用預設的字型和色彩服務的分類。  
  
- 預設字型和色彩伺服器中註冊的類別。  
  
- 建議特定的視窗藉由使用內建的顯示項目和類別目錄使用的 IDE`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer`和`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer`介面。  
  
  IDE 會使用產生的類別目錄為視窗的控制代碼。 類別目錄的名稱會顯示在**顯示設定：** 中的下拉式清單方塊**字型和色彩**屬性頁。  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>若要定義類別，使用內建的字型和色彩  
  
1. 建立任意的 GUID。  
  
    此 GUID 用來唯一識別類別<strong>。</strong> IDE 的預設字型和色彩的規格，此類別會重複使用。  
  
   > [!NOTE]
   > 當擷取使用的字型和色彩資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>或其他介面，Vspackage 會使用此 GUID 參考內建的資訊。  
  
2. 類別目錄的名稱必須加入 VSPackage 的資源 (.rc) 檔，在字串資料表，以便您可以在需要時顯示在 IDE 中當地語系化。  
  
    如需詳細資訊，請參閱 <<c0> [ 新增或刪除字串](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab)。  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>若要註冊分類，使用內建的字型和色彩  
  
1. 建構一種特殊的類別目錄中的下列位置的登錄項目：  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version>* \FontAndColors\\*\<Category>*]  
  
     *\<類別目錄 >* 是類別目錄的非當地語系化名稱。  
  
2. 填入登錄，以使用內建的字型和色彩配置具有四個值：  
  
    |名稱|類型|資料|描述|  
    |----------|----------|----------|-----------------|  
    |分類|REG_SZ|GUID|任意的 GUID，識別包含內建的字型和色彩配置的分類。|  
    |套件|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> 所有使用預設字型和色彩組態的 Vspackage 會使用此 GUID。|  
    |NameID|REG_DWORD|識別碼|在 VSPackage 中可當地語系化的類別目錄名稱的資源識別碼。|  
    |ToolWindowPackage|REG_SZ|GUID|VSPackage 實作的 GUID<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面。|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>若要起始使用系統提供的字型和色彩  
  
1. 建立的執行個體`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer`介面為視窗的實作和初始化的一部分。  
  
2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>方法，以取得的執行個體`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer`對應至目前的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>執行個體。  
  
3. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>兩次。  
  
   - 呼叫一次使用`VSEDITPROPID_ViewGeneral_ColorCategory`做為引數。  
  
   - 呼叫一次使用`VSEDITPROPID_ViewGeneral_FontCategory`做為引數。  
  
     這樣會設定並公開 （expose） 為視窗的屬性的預設字型和色彩的服務。  
  
## <a name="example"></a>範例  
 下列範例會起始將內建的字型和色彩。  
  
```  
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
 [使用字型和色彩](../extensibility/using-fonts-and-colors.md)   
 [取得字型和色彩資訊文字的顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)   
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)
