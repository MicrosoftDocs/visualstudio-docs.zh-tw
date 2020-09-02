---
title: 如何：存取內建字型和色彩配置 |Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685313"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>如何：存取內建字型和色彩配置
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 整合式開發環境 (IDE) 具有與編輯器視窗相關聯的字型和色彩配置。 您可以透過介面存取此配置 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。  
  
 若要使用內建字型和色彩配置，VSPackage 必須：  
  
- 定義要與預設字型和色彩服務搭配使用的類別。  
  
- 使用預設字型和色彩伺服器來註冊類別。  
  
- 使用和介面，通知 IDE 特定視窗使用內建的顯示專案和類別 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 。  
  
  IDE 會使用產生的類別做為視窗的控制碼。 類別目錄的名稱會顯示在 [字型**和色彩**] 屬性頁的 [**顯示設定：** ] 下拉式方塊中。  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>使用內建字型和色彩來定義分類  
  
1. 建立任意的 GUID。  
  
    此 GUID 是用來唯一識別類別目錄<strong>。</strong> 此類別會重複使用 IDE 的預設字型和色彩規格。  
  
   > [!NOTE]
   > 使用或其他介面來抓取字型和色彩資料時 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> ，vspackage 會使用此 GUID 來參考內建資訊。  
  
2. 類別目錄的名稱必須加入至 VSPackage 資源內的字串資料表 ( .rc) 檔，以便在 IDE 中顯示時，視需要進行當地語系化。  
  
    如需詳細資訊，請參閱 [新增或刪除字串](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab)。  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>使用內建字型和色彩註冊類別  
  
1. 在下列位置中，建立一種特殊類型的分類登錄專案：  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* 這是類別目錄的非當地語系化名稱。  
  
2. 填入登錄，以使用包含四個值的內建字型和色彩配置：  
  
    |名稱|類型|資料|描述|  
    |----------|----------|----------|-----------------|  
    |類別|REG_SZ|GUID|識別包含內建字型和色彩配置之類別目錄的任意 GUID。|  
    |套件|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> 所有使用預設字型和色彩設定的 Vspackage 都會使用此 GUID。|  
    |NameID|REG_DWORD|識別碼|VSPackage 中可當地語系化之分類名稱的資源識別碼。|  
    |ToolWindowPackage|REG_SZ|GUID|執行介面之 VSPackage 的 GUID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>起始使用系統提供的字型和色彩  
  
1. 在 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 視窗的執行和初始化過程中，建立介面的實例。  
  
2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 方法，以取得 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 對應到目前實例之介面的實例 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。  
  
3. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 兩次。  
  
   - 以引數的形式呼叫一次 `VSEDITPROPID_ViewGeneral_ColorCategory` 。  
  
   - 以引數的形式呼叫一次 `VSEDITPROPID_ViewGeneral_FontCategory` 。  
  
     這會將預設字型和色彩服務公開為視窗的屬性。  
  
## <a name="example"></a>範例  
 下列範例會起始使用內建字型和色彩。  
  
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
 [取得文字顏色標示的字型和色彩資訊](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)   
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)
