---
title: 列舉型別 （Visual Studio 偵錯） |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1cc4f811c1b1651d6ac5807f754a2d9c97eda2ad
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337890"
---
# <a name="enumerations-visual-studio-debugging"></a>Enumerations (Visual Studio Debugging)
以下是列舉型別供[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯 sdk 》。

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)指定如何解譯中的處理序識別碼[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構。

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)指定位址的類型。

- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)指定組件所在的位置。

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)指定偵錯引擎 (DE) 附加至程式節點的原因。

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)指定中斷點條件之暫止的樣式和繫結中斷點。

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)指定中斷點的錯誤類型。

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)提供可用來設定中斷點時，請指定其他資訊的選擇性旗標。

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md)列舉可用來設定中斷點時，請指定其他資訊的選擇性旗標的有效值。 這個列舉型別會擴充[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)列舉型別。

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)指定中斷點的中斷點要求的位置類型。

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)指定會導致引發中斷點的中斷點傳遞計數相關聯的條件。

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)指定是否要模擬資料中斷點或實作中的硬體。

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)指定繫結的中斷點和是否啟用的存在。

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)指定中斷點的程式碼位置，是一個資料位置，或是中斷點的另一種。

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)提供中斷點已繫結的原因。

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)指定要擷取失敗的解決方式的中斷點相關的資訊。

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)指定要擷取中斷點要求的相關資訊。

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md)列舉有效的值，指定要擷取有關中斷點要求的資訊。 這個列舉型別會擴充[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)列舉型別。

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)指定何種資訊是要擷取有關中斷點的成功解決方式。

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)用來判斷是否程式可能會停止在達到執行中的特定點之後執行。

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)值，指出用來偵錯伺服器和偵錯封裝之間進行通訊的通訊協定。

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)選取不同類型的建構函式。

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)指定的準則來比較兩個記憶體內容。

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)指定要擷取記憶體內容的相關資訊。

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)說明各種屬性[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)該[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面。

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)指定處理序已啟動偵錯，原因。

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)指定要擷取偵錯屬性物件的相關資訊。

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)指定要擷取偵錯參考物件的相關資訊。

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)指定反組譯碼的旗標。

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)指定要擷取反組譯碼欄位的相關資訊。

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)指定反組譯碼資料流的範圍。

- [DisplayKind](../../../extensibility/debugger/reference/displaykind.md)列舉有效的值，代表要從需要的資訊種類[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件，並向使用者顯示。

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)指定的準則來比較兩個文件內容。

- [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md)指定程式的狀態，傾印中有多少。

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)指定如何解譯的型別[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)代表的原因，編輯後繼續 不提供。

- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)指定控制運算式評估的旗標。

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md)列舉有效的控制運算式評估的旗標值。 這個列舉型別會擴充[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)列舉型別。

- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)指定事件屬性。

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)指定例外狀況狀態。

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)指定要擷取其相關的資訊[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)指定的欄位中包含種類[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件。

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md)列舉其他類型的欄位[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件可以包含。 這個列舉型別會擴充[FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)列舉型別。

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)指定的欄位型別修飾詞。

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)指定要擷取的堆疊框架物件有關的資訊。

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)指定的主機名稱類型。

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)指定要擷取檔案的名稱類型。

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)指定攔截例外狀況時要採取哪些動作。

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)指定要如何啟動程式。

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)指定何種資訊來擷取特定的機器。

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)用來描述機器。

- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)指定的訊息類型和原因。

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)用來描述模組。

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)指定偵錯模組資訊的旗標。

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)指定模組的符號的狀態。

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)選取來比對名稱大小寫的選項。

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)指定的運算式評估工具中的物件類型。

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)指定如何剖析的運算式。

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)指定暫止中斷點 （具有尚未已繫結中斷點） 的狀態。

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)指定暫止中斷點的狀態旗標。

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md)定義可以擷取有關連接埠提供者的中繼資料。

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)指定何種處理程序所擷取的資訊。

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)描述或指定的處理程序的屬性。

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)有效的列舉程式的值會終結旗標。

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)指定程式提供者相關聯的屬性。

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)指定所需屬性來取得從程式提供者。

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)指定參考的比較類型。

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)指定參考型別。

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)指定要啟動的反組譯碼中搜尋的位置。

- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)指定逐步執行的步驟類型。

- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)逐步執行指定間距單位。

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)指定要擷取的符號資訊的類型。

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)描述文件的屬性。

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)指定要擷取的執行緒相關資訊。

- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md)指定執行緒的狀態。

## <a name="requirements"></a>需求
 標頭： msdbg.h、 sh.h 或 ee.h

 命名空間：Microsoft.VisualStudio.Debugger.Interop

 組件︰Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)