---
title: " (Visual Studio 調試的列舉) |Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 45b26a6d5bc2a9bdb32d5a8412458e6a126486d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937123"
---
# <a name="enumerations-visual-studio-debugging"></a>Enumerations (Visual Studio Debugging)
以下是偵錯工具 SDK 的列舉 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 。

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) 指定如何解讀 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) 結構中的處理序識別碼。

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 指定位址的類型。

- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) 指定元件的所在位置。

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) 指定 debug engine (DE) 附加至程式節點的原因。

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) 指定暫止和系結中斷點的中斷點條件樣式。

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) 指定中斷點的錯誤類型。

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 提供選擇性旗標，可在設定中斷點時用來指定其他資訊。

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md) 列舉選擇性旗標的有效值，這個值可用來在設定中斷點時指定其他資訊。 此列舉會擴充 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) 列舉。

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) 指定中斷點要求之中斷點的位置類型。

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md) 指定與中斷點傳遞計數相關聯的條件，這會導致中斷點引發。

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) 指定是否要在硬體中模擬或執行資料中斷點。

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) 指定系結中斷點是否存在，以及是否已啟用。

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) 指定中斷點位於程式碼位置、是否為數據位置，或是另一種類型的中斷點。

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) 提供中斷點未系結的原因。

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) 指定要取得的資訊，以找出中斷點無法解析的問題。

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 指定要對中斷點要求取得哪些資訊。

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md) 列舉有效的值，指定要針對中斷點要求抓取的資訊。 此列舉會擴充 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) 列舉。

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md) 指定要對中斷點成功解決的相關資訊。

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 用來判斷程式是否可以在到達執行的特定點之後停止執行。

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md) 值，這個值表示要用來在偵錯工具伺服器與 debug 封裝之間進行通訊的通訊協定。

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) 選取不同類型的函式。

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) 指定比較兩個記憶體內容的準則。

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) 指定要對記憶體內容取得哪些資訊。

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) 描述 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 或 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 介面的各種屬性。

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md) 指定啟動處理常式以進行偵錯工具的原因。

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) 指定要取出哪些有關 debug 屬性物件的資訊。

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) 指定要針對 debug 參考物件取得哪些資訊。

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) 指定反組解碼的旗標。

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) 指定要對反組解碼欄位取得哪些資訊。

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) 指定反組解碼資料流程的範圍。

- [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) 列舉代表要從 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件取得並向使用者顯示之資訊類型的有效值。

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md) 指定用於比較兩個檔內容的準則。

- [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) 指定要傾印的程式狀態數量。

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) 指定如何解讀 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件的類型。

- [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) 表示無法使用 [編輯後繼續] 的原因。

- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 指定控制運算式評估的旗標。

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md) 列舉控制運算式評估之旗標的有效值。 此列舉會擴充 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) 列舉。

- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 指定事件屬性。

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) 指定例外狀況狀態。

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) 指定要對 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件取得哪些資訊。

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 指定 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件中所含的欄位種類。

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md) 列舉 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件可以包含的其他欄位類型。 此列舉會擴充 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 列舉。

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 指定欄位類型的修飾詞。

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md) 指定要針對堆疊框架物件取得的資訊。

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) 指定主機名稱的類型。

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 指定要取出之檔案的名稱類型。

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) 指定攔截例外狀況時要採取的動作。

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) 指定程式的啟動方式。

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) 指定要針對特定電腦取出的資訊類型。

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md) 用來描述電腦。

- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) 指定訊息類型和原因。

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md) 用來描述模組。

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) 指定 debug 模組資訊的旗標。

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) 指定模組的符號狀態。

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 選取相符名稱的案例選項。

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) 從運算式評估工具指定物件的類型。

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) 指定如何剖析運算式。

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md) 指定暫止中斷點的狀態 (尚未系結) 的中斷點。

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md) 指定暫止的中斷點狀態旗標。

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md) 定義可針對埠供應商抓取的中繼資料。

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) 指定要為進程取出的資訊種類。

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md) 描述或指定進程的屬性。

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md) 列舉程式損毀旗標的有效值。

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) 指定與程式提供者相關聯的屬性。

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) 指定要從程式提供者取得的所需屬性。

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md) 指定參考的比較類型。

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) 指定參考型別。

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) 指定要在反組解碼中開始搜尋的位置。

- [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 指定逐步執行的步驟類型。

- [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 指定逐步執行的步驟單位。

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) 指定要取出的符號資訊種類。

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md) 描述檔的屬性。

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md) 指定要抓取之執行緒的相關資訊。

- [THREADSTATE](../../../extensibility/debugger/reference/threadstate.md) 指定執行緒的狀態。

## <a name="requirements"></a>規格需求
 標頭： msdbg .h、sh. h 或 ee

 命名空間： VisualStudio

 元件： Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
