---
title: 結構和聯盟 |微軟文件
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 19d8f547d98488edffc6049be7619e5b5e921d93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713487"
---
# <a name="structures-and-unions"></a>Structures and Unions
以下是可視化工作室調試 SDK 中的結構和聯合。

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)指定程序識別碼,可以是系統 ID 或 GUID。

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)描述斷點將觸發的條件。

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)描述錯誤斷點的解析度,包括位置、程式和線程。

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)指定用於描述斷點位置的結構類型。

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)定義描述斷點在代碼中位址位置的元件。

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)描述直接綁定到正在調試的程式中的地址的斷點的位置。

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)描述代碼原始檔中行斷點的位置。

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)描述代碼中函數處斷點的偏移位置。

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)用於根據使用者可以從 IDE 輸入的字串設置代碼斷點。

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)用於設置基於使用者可以從 IDE 輸入的字串的數據斷點。

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)描述特定位置斷點的解析度。

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)描述以前傳遞斷點後將觸發斷點的計數和條件。

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)包含實現斷點所需的資訊。

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)包含實現斷點所需的資訊(與[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構相同,但包括供應商 GUID、約束和跟蹤點資訊)。

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)描述代碼斷點的位置。

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)描述綁定數據斷點的結果。

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)描述代碼斷點或數據斷點的邊界斷點資訊。

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)指定斷點解析度位置的結構。

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)描述字串陣列。

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)指定有關從元數據獲取的欄位類型的資訊。

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)描述對函數或方法的調用。

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)描述運行調試器的電腦。

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)描述 GUID 的清單。

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)描述記憶體上下文或程式碼上下文。

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)描述正在調試的程式中的位址。

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)表示多種不同類型的位址之一。

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)標識自定義查看器或類型可視化工具。

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)描述調試屬性,該屬性依次描述具有名稱、類型和值的分層性質的物件。

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)描述引用。

- [拆解資料](../../../extensibility/debugger/reference/disassemblydata.md)描述拆解到 IDE 以進行顯示。

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)描述正在調試的程式引發的異常或運行時錯誤。

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)描述局部變數、參數或其他欄位。

- [框架資訊](../../../extensibility/debugger/reference/frameinfo.md)描述堆疊幀。

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)描述可用調試引擎的唯一標識符陣列。

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)用於為模組設置 JustMyCode 資訊。

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)描述特定電腦。

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)描述陣列中的陣列元素。

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)描述類或結構欄位的位址。

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)描述作用域(通常是函數或方法)中的局部變數的位址。

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)描述類方法的位址。

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)描述方法或函數的參數。

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)描述方法或函數的返回值。

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)描述從元數據獲取的欄位類型。

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)描述特定模組(DLL、EXE 或程式集)。

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)描述有關已搜索的符號搜索路徑的狀態資訊。

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)描述本機位址。

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)描述從 PDB 符號獲取的欄位類型。

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)描述準備綁定到代碼位置的斷點的狀態。

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)描述流程。

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)描述表示程式節點的[IDebug ProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)物件的清單。

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)描述在電腦上運行的進程。

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)描述給定文本中的行和列位置。

- [執行緒屬性](../../../extensibility/debugger/reference/threadproperties.md)描述線程的屬性。

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)描述欄位的類型。

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)描述物理位址。

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)描述相對於`this`指標的位址(`Me`在可視化基本)。

## <a name="requirements"></a>需求
 標題: msdbg.h, sh.h 或 ee.h

 命名空間:微軟.VisualStudio.調試器.互通

 程式集:微軟.VisualStudio.除錯器.Interop.dll

## <a name="see-also"></a>另請參閱
- [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
