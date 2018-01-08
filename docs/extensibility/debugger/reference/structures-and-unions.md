---
title: "結構和等位 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1cae50d4ff122ebea1fa11291570ac23f556f6f5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="structures-and-unions"></a>結構和等位
以下是結構和等位在 Visual Studio 偵錯 SDK 中。  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 指定的處理序識別碼，這可能是系統識別碼或 GUID。  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 描述中斷點就會引發在其下的條件。  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 描述錯誤的中斷點，包括位置、 程式和執行緒的解析度。  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 指定用來描述中斷點的位置的結構類型。  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 定義元件的描述在程式碼中的位址中斷點的位置。  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 描述直接繫結正在偵錯的程式中的位址中斷點的位置。  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 描述在程式碼的原始程式檔中的行中斷點的位置。  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 描述中斷點在程式碼中的函式的位移的位置。  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 用於設定使用者可以輸入從 IDE 的字串為基礎的程式碼中斷點。  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 用於設定使用者可以輸入從 IDE 的字串為基礎的資料中斷點。  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 描述中斷點的特定位置的解析度。  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 描述將具有先前通過測試之後引發中斷點所在的計數和條件。  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 包含中斷點的實作所需的資訊。  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 包含中斷點的實作所需的資訊 (與相同[BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)結構但包含廠商 GUID、 條件約束和追蹤點的資訊)。  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 描述程式碼中斷點的位置。  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 描述繫結資料中斷點的結果。  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 描述程式碼中斷點或資料中斷點的繫結的中斷點資訊。  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 指定中斷點解析位置的結構。  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 描述字串的陣列。  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 指定取自中繼資料的欄位類型的相關資訊。  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 描述函式或方法的呼叫。  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 描述偵錯工具執行所在的電腦。  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 描述 Guid 的清單。  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 描述記憶體內容或程式碼內容。  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 描述偵錯程式中的位址。  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 代表一個位址的不同種類的數字。  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 識別自訂的檢視器，或輸入視覺化檢視。  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 描述偵錯屬性，依序描述階層式本質，具有名稱、 類型和值的物件。  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 描述的參考。  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 描述要顯示在 IDE 的反組譯碼。  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 描述例外狀況或程式偵錯時所擲回執行階段錯誤。  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 描述的本機變數、 參數或其他欄位。  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 描述堆疊框架。  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 描述可用的偵錯引擎的唯一識別碼的陣列。  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 用來設定 JustMyCode 模組的資訊。  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 描述特定電腦。  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 描述在陣列中的陣列項目。  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 描述類別或結構的欄位的位址。  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 描述 （通常是函式或方法） 的範圍內的區域變數的位址。  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 描述類別的方法的位址。  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 描述的方法或函式的參數。  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 描述之方法或函式的傳回值。  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 描述從中繼資料的欄位型別。  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 描述特定模組 （DLL、 EXE 或組件）。  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 描述符號搜尋路徑中搜尋的相關狀態資訊。  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 描述原生位址。  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 描述取自 PDB 符號的欄位型別。  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 說明準備好要繫結至程式碼位置的中斷點的狀態。  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 描述程序。  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 描述一份[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)程式節點表示的物件。  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 描述在電腦上執行的程序。  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 描述給定文字中的行和資料行位置。  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 描述執行緒屬性。  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 描述欄位的類型。  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 描述實體的位址。  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 描述的相對位址，`this`指標 (`Me`在 Visual Basic 中)。  
  
## <a name="requirements"></a>需求  
 標頭： msdbg.h、 sh.h 或 ee.h  
  
 命名空間： Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>請參閱  
 [API 參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)