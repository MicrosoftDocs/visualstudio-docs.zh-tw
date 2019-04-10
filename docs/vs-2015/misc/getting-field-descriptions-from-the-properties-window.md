---
title: 從 [屬性] 視窗中取得欄位描述 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 0fa07029ee1b96f3b8f1328d654b4d5d83953142
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58945136"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>從 [屬性] 視窗中取得欄位描述
在 [屬性]  視窗底部的描述區域會顯示選取的屬性欄位相關資訊。 這項功能預設為開啟。 如果想要隱藏描述欄位，請以滑鼠右鍵按一下 [屬性]  視窗，然後按一下 [描述] 。 這樣也會移除功能表視窗之 [描述]  標題旁的核取記號。 只要依照相同的步驟切換 [描述]  ，就可以再次顯示欄位。  
  
 描述欄位中的資訊出自 <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>。 每個方法、介面、coclass 等在類型程式庫中都可以有未當地語系化的 `helpstring` 屬性。 **屬性**視窗中擷取的字串<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>。  
  
### <a name="to-specify-localized-help-strings"></a>指定當地語系化的說明字串  
  
1. 請將 `helpstringdll` 屬性加入類型程式庫 (`typelib`) 的 library 陳述式。  
  
   > [!NOTE]
   >  如果類型程式庫位於物件程式庫 (.olb) 檔案中，這個步驟就是選擇性的。  
  
2. 為字串指定 `helpstringcontext` 屬性。 您也可以指定 `helpstring` 屬性。  
  
    這些屬性與 `helpfile` 和 `helpcontext` 屬性不同，它們位在說明主題的實際 .chm 檔案中。  
  
   若要擷取描述資訊，以顯示反白顯示的屬性名稱，**屬性**視窗呼叫<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A>已選取的屬性，指定想要`lcid`屬性輸出字串。 對內，<xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> 會尋找 `helpstringdll` 屬性中指定的 .dll 檔案，並以指定的內容和 `lcid` 屬性呼叫 .dll 檔案的 `DLLGetDocumentation`。  
  
   `DLLGetDocumentation` 的特徵標記和實作是：  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
  `DLLGetDocumentation` 函式必須是 .def 檔案中為 DLL 定義的匯出。  
  
 對內建立的 .olb 檔案，其實是個 DLL。 這個 DLL 包含一項資源、類型程式庫 (.tlb) 檔案，以及匯出的函式 `DLLGetDocumentation`。  
  
 如果是 .olb 檔案， `helpstringdll` 屬性即是選擇性的，因為它是包含了 .tlb 檔案本身的同一個檔案。  
  
 若要取得在 [描述]  窗格中顯示的字串，您至少要在類型程式庫中指定 `helpstring` 屬性。 如果希望當地語系化這些字串，您必須指定 `helpstringdll` (選擇性) 屬性和 `helpstringcontext` (必要) 屬性並實作 `DLLGetDocumentation`。  
  
 透過 idl 的 `helpstringcontext` 屬性和 `DLLGetDocumentation`取得當地語系化資訊時，不必實作其他介面。  
  
 取得屬性的當地語系化名稱和說明的另一個方式，是實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>。 如需實作這個方法的詳細資訊，請參閱 [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Properties Window Fields and 介面](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [擴充屬性](../extensibility/internals/extending-properties.md)   
 [helpstringdll](http://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [helpstring](http://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](http://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [helpcontext](http://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [helpfile](http://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](http://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)