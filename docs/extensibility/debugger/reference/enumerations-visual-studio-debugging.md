---
title: 枚舉(可視化工作室調試) |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- enumerations [Visual Studio SDK]
- debugging [Debugging SDK], enumerations
ms.assetid: 557065bf-081f-4d57-8744-bae02b8a5a6e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80ad4db1090857d87e28d90d8478fbdea0905e86
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737133"
---
# <a name="enumerations-visual-studio-debugging"></a>Enumerations (Visual Studio Debugging)
以下是調試 SDK[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]的 枚舉。

- [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)指定如何在[AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)結構中解釋進程 ID。

- [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)指定位址的類型。

- [程式集分解](../../../extensibility/debugger/reference/assemblylocresolution.md)指定程式集的位置。

- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)指定除錯引擎 (DE) 附加到程式節點的原因。

- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)指定掛起和綁定斷點的斷點條件樣式。

- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)指定斷點的錯誤類型。

- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)提供可選標誌,用於在設置斷點時指定其他資訊。

- [BP_FLAGS90](../../../extensibility/debugger/reference/bp-flags90.md)枚舉可選標誌的有效值,這些標記可用於在設置斷點時指定其他資訊。 此枚舉擴展了[BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)枚舉。

- [BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md)指定斷點請求的斷點的位置類型。

- [BP_PASSCOUNT_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)指定與斷點通過計數關聯的條件,這將導致斷點觸發。

- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)指定數據斷點是在硬體中模擬還是實現。

- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)指定綁定斷點是否存在以及是否啟用了該斷點。

- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)指定斷點是位於代碼位置、資料位置還是其他類型的斷點。

- [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)給出斷點未綁定的原因。

- [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md)指定要檢索的關於斷點解析失敗的資訊。

- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)指定要檢索的關於斷點請求的資訊。

- [BPREQI_FIELDS90](../../../extensibility/debugger/reference/bpreqi-fields90.md)枚舉指定要檢索的關於斷點請求的資訊的有效值。 此枚舉擴展了[BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)枚舉。

- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)指定要檢索哪些有關斷點成功解析的資訊。

- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)用於確定程式在到達執行中的特定點后是否可以停止執行。

- [CONNECTION_PROTOCOL](../../../extensibility/debugger/reference/connection-protocol.md)指示用於在調試伺服器和調試包之間通信的協議的值。

- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)選擇不同類型的構造函數。

- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)指定比較兩個記憶體上下文的條件。

- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)指定要檢索有關記憶體上下文的資訊。

- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)描述[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)或[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)介面的各種屬性。

- [DEBUG_REASON](../../../extensibility/debugger/reference/debug-reason.md)指定啟動進程以進行調試的原因。

- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)指定要檢索的有關調試屬性物件的哪些資訊。

- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)指定要檢索的有關調試引用物件的哪些資訊。

- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)指定拆卸的標誌。

- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)指定要檢索的有關拆解欄位的資訊。

- [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)指定拆解流的範圍。

- [顯示金德](../../../extensibility/debugger/reference/displaykind.md)枚舉表示要從[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件獲取的資訊類型並顯示給使用者的有效值。

- [DOCCONTEXT_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)指定比較兩個文檔上下文的條件。

- [傾印型別](../../../extensibility/debugger/reference/dumptype.md)指定要轉儲的程式狀態。

- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)指定如何解釋[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件的類型。

- [恩奇不可用原因](../../../extensibility/debugger/reference/encunavailablereason.md)表示"編輯"和"繼續"不可用的原因。

- [埃瓦爾克](../../../extensibility/debugger/reference/evalflags.md)指定控制表達式計算的標誌。

- [EVALFLAGS90](../../../extensibility/debugger/reference/evalflags90.md)枚舉控制運算式計算的標誌的有效值。 此枚舉擴展了[EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)枚舉。

- [事件屬性](../../../extensibility/debugger/reference/eventattributes.md)指定事件屬性。

- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)指定異常狀態。

- [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)指定要檢索的關於[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件的資訊。

- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)指定[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件中包含的欄位類型。

- [FIELD_KIND_EX](../../../extensibility/debugger/reference/field-kind-ex.md)枚舉[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)物件可以包含的其他類型的欄位。 此枚舉擴展[了FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)枚舉。

- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)指定欄位型別的修飾符。

- [FRAMEINFO_FLAGS](../../../extensibility/debugger/reference/frameinfo-flags.md)指定要檢索有關堆疊幀物件的資訊。

- [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)指定主機名的類型。

- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)指定要檢索的檔案的名稱類型。

- [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)指定在攔截異常時要執行的操作。

- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)指定如何啟動程式。

- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)指定要檢索特定計算機的資訊類型。

- [MACHINE_INFO_FLAGS](../../../extensibility/debugger/reference/machine-info-flags.md)用於描述機器。

- [訊息類型](../../../extensibility/debugger/reference/messagetype.md)指定消息類型和原因。

- [MODULE_FLAGS](../../../extensibility/debugger/reference/module-flags.md)用於描述模組。

- [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)指定除錯模組資訊的標誌。

- [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)指定模組的符號狀態。

- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)選擇匹配名稱的案例選項。

- [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md)從表達式賦值器指定對象的類型。

- [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)指定如何解析表達式。

- [PENDING_BP_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)指定掛起斷點的狀態(尚未綁定的斷點)。

- [PENDING_BP_STATE_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)指定掛起的斷點狀態標誌。

- [PORT_SUPPLIER_DESCRIPTION_FLAGS](../../../extensibility/debugger/reference/port-supplier-description-flags.md)定義可以檢索的關於埠供應商的元數據。

- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)指定要檢索進程的資訊類型。

- [PROCESS_INFO_FLAGS](../../../extensibility/debugger/reference/process-info-flags.md)描述或指定進程的屬性。

- [PROGRAM_DESTROY_FLAGS](../../../extensibility/debugger/reference/program-destroy-flags.md)枚舉程式的有效值銷毀標誌。

- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)指定與程式提供程式關聯的屬性。

- [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)指定從程式提供程式獲取的所需屬性。

- [REFERENCE_COMPARE](../../../extensibility/debugger/reference/reference-compare.md)指定引用的比較類型。

- [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)指定引用類型。

- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)指定在拆解中開始查找的位置。

- [步進](../../../extensibility/debugger/reference/stepkind.md)指定步進的步驟類型。

- [步進單元](../../../extensibility/debugger/reference/stepunit.md)指定步進的步驟單元。

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)指定要檢索的符號資訊類型。

- [TEXT_DOC_ATTR_2](../../../extensibility/debugger/reference/text-doc-attr-2.md)描述文件的屬性。

- [THREADPROPERTY_FIELDS](../../../extensibility/debugger/reference/threadproperty-fields.md)指定有關要檢索的線程的資訊。

- [執行緒狀態](../../../extensibility/debugger/reference/threadstate.md)指定線程的狀態。

## <a name="requirements"></a>需求
 標題: msdbg.h, sh.h 或 ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
