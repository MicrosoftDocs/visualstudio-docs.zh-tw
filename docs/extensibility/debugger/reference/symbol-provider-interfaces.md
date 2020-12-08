---
title: 符號提供者介面 |Microsoft Docs
description: 本文將連結至 Visual Studio SDK 的符號處理介面描述，此介面會在中斷模式期間評估呼叫堆疊中的變數。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- interfaces, symbol handler
- symbol handler, interfaces
- symbol handler, evaluating variables
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a24baec6738382f93dee5d8b7843d624eea80890
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845787"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
以下是的符號處理介面 [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] 。

## <a name="discussion"></a>討論
 在中斷模式期間，這些介面是用來評估呼叫堆疊中的變數。 它們只會在 (SP) 的 common language runtime 符號提供者上執行。

|介面|實作為|描述|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|表示專案的位址。|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|代表專案的位址，提供處理序識別碼的存取權。|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|表示陣列符號或陣列類型。|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|表示類別符號或類別類型。|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|表示具有 managed 程式碼專屬方法的 COM + 符號提供者。|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|以 managed 程式碼專屬的方法表示 COM + 符號提供者，並擴充 **IDebugComPlusSymbolProvider**。|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|代表做為其他符號或類型之容器的符號或類型。|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|表示可以附加至符號的自訂屬性。|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|表示方法或型別上的自訂屬性查詢。|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|提供符號上自訂屬性的存取權。|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|可在執行時間決定之任何類型的基底介面。|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|表示 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) 物件的動態欄位。|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|表示列舉型別。|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|擴充可用欄位的類型，以支援 managed 程式碼泛型。|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|所有欄位的基類;表示符號或類型的描述。|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|代表 managed 程式碼泛型型別的欄位定義。|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|代表 managed 程式碼泛型型別的欄位實例。|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|代表 managed 程式碼泛型型別的參數。|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|表示方法。|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|表示 debug 選擇性修飾詞。|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|表示指標。|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|表示來自 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 介面的基本類型列舉值。|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|表示可以取得或設定之 managed 程式碼類別的屬性。|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|代表提供符號和類型的符號提供者。|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|代表可直接存取中繼資料和核心符號介面的符號提供者。|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|表示建立代表型別之欄位的能力。|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|擴充 **IDebugTypeFieldBuilder** ，以便能夠建立陣列類型。|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|代表 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件的集合。|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|代表 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 物件的集合。|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|代表 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件的集合。|

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
