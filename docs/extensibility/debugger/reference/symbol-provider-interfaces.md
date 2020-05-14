---
title: 符號提供程式介面 |微軟文件
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
ms.openlocfilehash: 7929ba36c76f0db1cabab087afe3590de509efff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715843"
---
# <a name="symbol-provider-interfaces"></a>Symbol Provider Interfaces
以下是的[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]符號處理介面。

## <a name="discussion"></a>討論區
 這些介面用於在中斷模式下計算調用堆疊中的變數。 它們僅為通用語言運行時符號提供程式 (SP) 實現。

|介面|實施者|描述|
|---------------|--------------------|-----------------|
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|SP|表示項的位址。|
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|SP|表示項的位址,提供對進程 ID 的訪問。|
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|SP|表示陣列符號或數位類型。|
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|SP|表示類符號或類類型。|
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|SP|表示具有特定於託管代碼的方法的 COM+ 符號提供程式。|
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|SP|表示 COM+ 符號提供者,其方法特定於託管代碼並擴展**IDebugComPlusSymbol 提供者**。|
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|SP|表示作為其他符號或類型的容器的符號或類型。|
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|SP|表示可以附加到符號的自定義屬性。|
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|SP|表示對方法或類型的自定義屬性的查詢。|
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|SP|提供對符號上的自定義屬性的訪問。|
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|SP|可在運行時確定的任何類型的基本介面。|
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|SP|表示[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件的動態欄位。|
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|SP|表示列舉型別。|
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|Sp|擴展可用欄位的類型以支援託管代碼泛型。|
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|SP|所有欄位的基類;表示符號或類型的說明。|
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|SP|表示託管代碼泛型類型的欄位的定義。|
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|SP|表示託管代碼泛型類型的欄位的實例。|
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|SP|表示託管代碼泛型類型的參數。|
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|SP|表示方法。|
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|SP|表示調試可選修改器。|
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|SP|表示指標。|
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|SP|表示[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面中的原始類型枚舉值。|
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|SP|表示可以獲取或設置的託管代碼類的屬性。|
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|SP|表示提供符號和類型的符號提供程式。|
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|SP|表示直接存取中繼資料和核心符號介面的符號提供程式。|
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|SP|表示創建表示類型的欄位的能力。|
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|SP|擴展**IDebugTypeFieldBuilder,** 以便能夠建立陣列類型。|
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|SP|表示[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)物件的集合。|
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|SP|表示[IDebugCustom 屬性物件](../../../extensibility/debugger/reference/idebugcustomattribute.md)的集合。|
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|SP|表示[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件的集合。|

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
