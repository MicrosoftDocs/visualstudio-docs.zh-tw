---
title: "符號提供者介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f2b3ec92ce76a3218c646c51ccb28d99322baf93
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="symbol-provider-interfaces"></a>符號提供者介面
以下是符號處理介面[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]。  
  
## <a name="discussion"></a>討論  
 這些介面可用來評估在中斷模式期間的呼叫堆疊中的變數。 它們被實作只有通用語言執行階段的符號提供者 (SP)。  
  
|介面|由實作|描述|  
|---------------|--------------------|-----------------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|代表項目的位址。|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|代表位址的項目，提供存取的處理序識別碼。|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|代表符號陣列或陣列型別。|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|代表類別符號或類別類型。|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|代表 COM + 符號提供者所特有的 managed 程式碼的方法。|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|代表 COM + 符號提供者所特有的 managed 程式碼的方法，並擴充**IDebugComPlusSymbolProvider**。|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|代表符號或其他符號或類型的容器類型。|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|表示可附加至符號自訂屬性。|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|表示在方法或類型的自訂屬性的查詢。|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|提供存取自訂屬性的符號上。|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|可以在執行階段決定的任何類型的基底介面。|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|代表動態欄位[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|表示列舉型別。|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|預存程序|擴充可用欄位以支援 managed 程式碼的泛型的類型。|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|基底類別的所有欄位。代表符號或類型的描述。|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|表示欄位的 managed 程式碼的泛型類型定義。|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|表示欄位的 managed 程式碼的泛型型別執行個體。|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|代表 managed 程式碼的泛型類型的參數。|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|表示的方法。|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|表示偵錯的選擇性修飾詞。|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|表示的指標。|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|表示基本類型列舉值從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|代表 managed 程式碼類別，可取得或設定的屬性。|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|表示提供符號和類型的符號提供者。|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|表示中繼資料和核心符號介面直接存取的符號提供者。|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|表示能夠建立代表類型的欄位。|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|擴充**IDebugTypeFieldBuilder**能夠建立陣列類型。|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|代表集合[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件。|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|代表集合[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)物件。|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|代表集合[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。|  
  
## <a name="see-also"></a>請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)