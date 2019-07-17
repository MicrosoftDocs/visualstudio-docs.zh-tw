---
title: 符號提供者介面 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c409175fb39207bc0e83a521577ad6d641731691
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204862"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

以下是符號處理介面[!INCLUDE[vsipsdk](../../../includes/vsipsdk-md.md)]。  
  
## <a name="discussion"></a>討論  
 這些介面用來評估在中斷模式期間的呼叫堆疊中的變數。 它們只針對通用語言執行階段的符號提供者 (SP) 進行實作。  
  
|介面|藉由將|描述|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|表示項目的位址。|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|代表地址的項目，提供存取的處理序識別碼。|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|代表陣列符號或陣列型別。|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|代表類別符號或類別類型。|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|代表 COM + 符號提供者特有的 managed 程式碼的方法。|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|代表 COM + 符號提供者特有的 managed 程式碼的方法，並延伸**IDebugComPlusSymbolProvider**。|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|代表符號或其他符號或類型的容器型別。|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|表示可附加至符號自訂屬性。|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|表示在方法或類型的自訂屬性的查詢。|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|提供存取自訂屬性的符號上。|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|可以在執行階段決定任何類型的基底介面。|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|代表動態欄位[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|表示列舉型別。|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|預存程序|擴充可用的欄位，以支援 managed 程式碼的泛型的類型。|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|所有的欄位; 基底類別代表符號或類型的描述。|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|代表 managed 程式碼的泛型類型的欄位定義。|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|表示欄位的 managed 程式碼的泛型型別執行個體。|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|表示 managed 程式碼的泛型類型參數。|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|表示的方法。|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|表示偵錯的選擇性修飾詞。|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|表示的指標。|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|表示基本類型列舉值從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|表示 managed 程式碼類別，可取得或設定屬性。|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|表示提供符號和類型的符號提供者。|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|表示中繼資料和核心符號介面直接存取的符號提供者。|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|表示建立的欄位，表示類型的能力。|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|擴充**IDebugTypeFieldBuilder**能夠建立陣列的型別。|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|表示的集合[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|表示的集合[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)物件。|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|表示的集合[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。|  
  
## <a name="see-also"></a>另請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
