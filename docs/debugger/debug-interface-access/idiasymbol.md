---
title: IDiaSymbol |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol interface
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a456abd2d3d80a122d4182ae882ca28b07788596
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479090"
---
# <a name="idiasymbol"></a>IDiaSymbol
描述符號的執行個體的屬性。  
  
## <a name="syntax"></a>語法  
  
```  
IDiaSymbol : IUnknown  
```  
  
## <a name="methods-in-alphabetical-order"></a>依照依字母順序排列順序的方法  
 下表顯示的方法`IDiaSymbol`。  
  
> [!NOTE]
>  符號會傳回有意義的資料，只是某些一種方法，根據符號的類型。 如果方法傳回`S_OK`，則該方法具有傳回有意義的資料。  
  
|方法|描述|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|擷取所有子系的符號。|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|擷取符號的子系。 這個方法是擴充的版本[idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)。|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|擷取在指定的位址是有效的符號的子系。|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|擷取在指定的相對虛擬位址 (RVA) 的有效符號的子系。|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|擷取在指定的虛擬位址是有效的符號的子系。|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|擷取列舉，可讓用戶端來逐一查看所有指定的位址上的內嵌框架。|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|擷取列舉，可讓用戶端來逐一查看所有指定相對虛擬位址 (RVA) 上的內嵌框架。|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|擷取列舉，可讓用戶端來逐一查看所有指定的虛擬位址 (VA) 上的內嵌框架。|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|擷取可讓用戶端來逐一查看的所有函式內嵌，直接或間接地在這個符號的行號資訊的列舉。|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|擷取可讓用戶端來逐一查看的是內嵌的直接或間接指定的位址範圍內的這個符號中的所有函式的行號資訊的列舉。|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|擷取可讓用戶端來逐一查看的是內嵌的直接或間接指定相對的虛擬位址 (RVA) 中的這個符號中的所有函式的行號資訊的列舉。|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|擷取可讓用戶端來逐一查看的是內嵌的直接或間接，此符號內指定的虛擬位址 (VA) 中的所有函式的行號資訊的列舉。|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|指定對應的標記值，這個方法會傳回包含符號的列舉型別在這個虛設常式函式，在指定的相對虛擬位址。|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|虛設常式函式 c + + AMP 中傳回 accelerator 指標標記數目。|  
|[IDiaSymbol::get_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|傳回所有 accelerator 指標的標記值對應至 c + + AMP 加速器虛設常式函式。|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|擷取的類別成員的存取修飾詞。|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|擷取位址位置的位移的部分。|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|擷取位址位置中區段的一部分。|  
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|擷取表示另一個符號是否參考這個位址的旗標。|  
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|擷取的程式資料庫的存在時間值。|  
|[IDiaSymbol::get_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|擷取陣列索引類型的符號識別項。|  
|[IDiaSymbol::get_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|擷取符號的陣列索引類型識別碼。|  
|[IDiaSymbol::get_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|擷取後端的主要版本號碼。|  
|[IDiaSymbol::get_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|擷取後端次要版本號碼。|  
|[IDiaSymbol::get_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|擷取後端組建編號。|  
|[IDiaSymbol::get_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|擷取的基底的資料位移。|  
|[IDiaSymbol::get_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|擷取基底的資料位置。|  
|[IDiaSymbol::get_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|擷取要從中指標為基礎的符號。|  
|[IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|擷取要從中指標為基礎的符號 ID。|  
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|擷取類型標記的簡單類型。|  
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|擷取位置的位元位置。|  
|[IDiaSymbol::get_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|擷取的 HLSL 類型內建類型。|  
|[IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|傳回方法的呼叫慣例的指標。|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|擷取類別的父系符號的參考。|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|擷取的符號類別父識別碼。|  
|[IDiaSymbol::get_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|擷取表示符號是否參考程式碼位址的旗標。|  
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|擷取表示符號是否編譯器產生的旗標。|  
|[IDiaSymbol::get_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|擷取編譯器用來建立名稱[編譯](../../debugger/debug-interface-access/compiland.md)。|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|擷取表示使用者定義資料類型是否具有建構函式的旗標。|  
|[IDiaSymbol::get_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|擷取包含此符號的符號。|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|擷取旗標，指出是否在使用者定義資料類型常數。|  
|[IDiaSymbol::get_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|擷取清單或陣列中的項目數目。|  
|[IDiaSymbol::get_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|擷取有效的位址範圍相關聯的本機符號數目。|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|擷取旗標，指出是否此函數會使用自訂的呼叫慣例。|  
|[IDiaSymbol::get_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|擷取 OEM 符號的資料位元組。|  
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|擷取變數的分類資料符號。|  
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|擷取描述之已編譯的程式的單元的 編輯後繼續功能旗標。|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|擷取指出是否使用目前傳回函式的旗標。|  
|[IDiaSymbol::get_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|擷取前端的主要版本號碼。|  
|[IDiaSymbol::get_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|擷取的前端的次要版本號碼。|  
|[IDiaSymbol::get_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|擷取的前端的組建編號。|  
|[IDiaSymbol::get_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|擷取表示公用符號是否參考的函式的旗標。|  
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|擷取符號的 GUID。|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|擷取旗標，指出函數是否包含呼叫`alloca`。|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|擷取表示使用者定義資料類型是否有任何定義的指派運算子的旗標。|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|擷取表示使用者定義資料類型是否有定義任何轉型運算子的旗標。|  
|[IDiaSymbol::get_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|擷取指出編譯模組是否包含任何偵錯資訊的旗標。|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|擷取指出函數是否具有 c + +-樣式例外狀況處理常式的旗標。|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|擷取指出函數是否具有非同步例外狀況處理常式的旗標。|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|擷取指出函數是否具有內嵌組譯碼的旗標。|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|擷取指出函數是否包含 longjmp 命令 （C 樣式例外狀況處理的一部分） 的旗標。|  
|[IDiaSymbol::get_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|擷取旗標，指出模組是否包含 managed 程式碼。|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|擷取表示使用者定義資料類型是否有巢狀型別定義的旗標。|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|擷取表示函式或編譯單位已編譯的安全性檢查的旗標 (透過[/GS （緩衝區安全性檢查）](/cpp/build/reference/gs-buffer-security-check)編譯器參數)。|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|擷取指出函數是否具有 Win32 樣式的結構化例外狀況處理的旗標。|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|擷取指出函數是否包含 setjmp 命令旗標。|  
|[IDiaSymbol::get_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|擷取旗標，指出是否在使用者定義資料類型為間接虛擬基底類別。|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|擷取指出函數是否已標記為內嵌屬性的旗標。|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|擷取指出函數是否有從中斷指令傳回的旗標。|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|擷取指出函數是否為基底類別虛擬函式的旗標。|  
|[IDiaSymbol::get_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|擷取表示符號是否與共用本機群組的變數在編譯 c + + AMP 加速器的程式碼對應的旗標。|  
|[IDiaSymbol::get_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|擷取表示符號是否與對應的旗標*定義範圍符號*標記元件在編譯 c + + AMP 加速器的程式碼指標變數。 定義範圍符號就是位址的範圍變數的位置。|  
|[IDiaSymbol::get_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|指出是否符號對應至最上層函式符號的著色器編譯對應於 accelerator`parallel_for_each`呼叫。|  
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|擷取旗標，指出資料是否為彙總的多個符號之一部分。|  
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|擷取表示符號檔是否包含 C 類型的旗標。|  
|[IDiaSymbol::get_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|擷取指出模組是否已轉換成原生程式碼的從通用的中繼語言 (CIL) 的旗標。|  
|[IDiaSymbol::get_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|擷取表示使用者定義資料類型的項目是否對齊，以特定界限的旗標。|  
|[IDiaSymbol::get_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|指定這個符號表示高等級著色器語言 」 (HLSL) 資料。|  
|[IDiaSymbol::get_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|擷取旗標，指出是否已編譯的模組[/hotpatch （建立可線上修補的影像）](/cpp/build/reference/hotpatch-create-hotpatchable-image)編譯器參數。|  
|[IDiaSymbol::get_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|擷取旗標，表示與 LTCG 連結器是否已連結的受管理的編譯。|  
|[IDiaSymbol::get_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|指定的矩陣是否為主要的資料列。|  
|[IDiaSymbol::get_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|擷取指出受管理的編譯模組是否.netmodule （包含只有中繼資料） 的旗標。|  
|[IDiaSymbol::get_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|指定是否`this`指標會指向具有多重繼承的資料成員。|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|擷取旗標，指出函數是否具有[naked](/cpp/cpp/naked-cpp)屬性。|  
|[IDiaSymbol::get_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|指定是否要立即最佳化變數。|  
|[IDiaSymbol::get_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|指定是否`this`指標為基礎的符號值。|  
|[IDiaSymbol::get_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|指定這個符號是否為資料成員的指標。|  
|[IDiaSymbol::get_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|指定這個符號是否為成員函式的指標。|  
|[IDiaSymbol::get_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|指定是否將變數會有傳回值。|  
|[IDiaSymbol::get_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|指定是否使用 /SDL 選項編譯的模組。|  
|[IDiaSymbol::get_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|指定是否`this`指標會指向資料成員的單一繼承。|  
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|擷取旗標，指出資料是否已分割成不同的符號的彙總。|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|擷取旗標，指出是否為靜態函式或 thunk 的圖層。|  
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|擷取表示是否有符號檔中已移除專用符號的旗標。|  
|[IDiaSymbol::get_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|指定是否`this`指標會指向資料成員的虛擬繼承。|  
|[IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|擷取來源的語言。|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|擷取這個符號所表示之物件所使用的記憶體位元組數目。|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|擷取語彙的父代符號的參考。|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|擷取符號的語彙的父識別碼。|  
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|擷取的文件庫或物件檔案載入物件的檔案名稱。|  
|[IDiaSymbol::get_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|傳回本機符號是有效的位址範圍的長度。|  
|[IDiaSymbol::get_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|傳回本機符號無效的起始位址範圍中區段的一部分。|  
|[IDiaSymbol::get_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|傳回本機符號無效的起始位址範圍的位移的部分。|  
|[IDiaSymbol::get_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|傳回本機符號是有效的位址範圍開頭。|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|擷取資料符號的位置類型。|  
|[IDiaSymbol::get_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|擷取 FORTRAN 陣列維度的下限。|  
|[IDiaSymbol::get_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|擷取 FORTRAN 陣列維度的下限符號識別的項。|  
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|擷取目標 CPU 的類型。|  
|[IDiaSymbol::get_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|擷取表示符號是否參考到 managed 程式碼的旗標。|  
|[IDiaSymbol::get_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|擷取記憶體空間類型。|  
|[IDiaSymbol::get_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|擷取表示符號是否是指 Microsoft Intermediate Language (MSIL) 程式碼的旗標。|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|擷取的符號名稱。|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|擷取旗標，指出是否在使用者定義資料類型巢狀處理。|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|擷取旗標，指出是否要將函式標記與[noinline](/cpp/cpp/noinline)屬性。|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|擷取表示是否與宣告的函式的旗標[noreturn](/cpp/cpp/noreturn)屬性。|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|擷取旗標，指出是否沒有堆疊順序無法完成，因為堆疊緩衝區檢查的一部分。|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|擷取表示是否函式或標籤永遠不會達到的旗標。|  
|[IDiaSymbol::get_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|虛設常式函式 c + + AMP 中傳回 accelerator 指標標記數目。|  
|[IDiaSymbol::get_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|擷取會套用至原始類型的修飾詞數目。|  
|[IDiaSymbol::get_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|擷取註冊索引鍵的數目。|  
|[IDiaSymbol::get_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|擷取在矩陣中的資料列數目。|  
|[IDiaSymbol::get_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|擷取在矩陣中的資料行數目。|  
|[IDiaSymbol::get_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|取得物件的檔案名稱。|  
|[IDiaSymbol::get_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|擷取物件的指標類別方法的型別。|  
|[IDiaSymbol::get_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|擷取的符號`oemId`值。|  
|[IDiaSymbol::get_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|擷取的符號`oemSymbolId`值。|  
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|擷取符號位置的位移。|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|擷取旗標，以指定的函式或標籤包含最佳化程式碼也做為偵錯資訊。|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|擷取表示使用者定義資料類型是否具有多載運算子的旗標。|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|擷取旗標，指出是否已壓縮的使用者定義資料類型。|  
|[IDiaSymbol::get_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|擷取已編譯的程式或編譯單位時的平台類型。|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|擷取旗標，指出函式純虛擬。|  
|[IDiaSymbol::get_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|擷取 FORTRAN 多維陣列的陣序規範。|  
|[IDiaSymbol::get_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|擷取旗標，指出是否為指標類型為參考。|  
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|擷取位置的登錄指示項。|  
|[IDiaSymbol::get_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|擷取註冊型別。|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|擷取位置的相對虛擬位址 (RVA)。|  
|[IDiaSymbol::get_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|指定是否`this`指標加上旗標限制。|  
|[IDiaSymbol::get_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|擷取的取樣器的位置。|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|擷取表示是否在使用者定義資料類型會出現在所語彙範圍的旗標。|  
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|擷取符號的簽章值。|  
|[IDiaSymbol::get_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|擷取的使用者定義型別之成員的大小。|  
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|擷取位置的位置數目。|  
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|擷取原始程式檔的檔案名稱。|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|擷取指出指定的使用者定義型別定義所在的來源檔案和行號。|  
|[IDiaSymbol::get_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|擷取 strided 陣列之矩陣的分散。|  
|[IDiaSymbol::get_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|擷取的子型別。|  
|[IDiaSymbol::get_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|擷取子類型識別碼。|  
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|擷取要從中載入符號檔的名稱。|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|擷取唯一符號識別項。|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|擷取符號類型分類。|  
|[IDiaSymbol::get_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|擷取的 thunk 目標位移的區段。|  
|[IDiaSymbol::get_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|擷取 thunk 目標的相對虛擬位址 (RVA)。|  
|[IDiaSymbol::get_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|擷取 thunk 目標位址 > 一的節。|  
|[IDiaSymbol::get_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|擷取 thunk 目標的虛擬位址 (VA)。|  
|[IDiaSymbol::get_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|擷取紋理位置。|  
|[IDiaSymbol::get_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|擷取邏輯`this`adjustor 方法。|  
|[IDiaSymbol::get_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|擷取函式的 thunk 類型。|  
|[IDiaSymbol::get_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|擷取基礎可執行檔的時間戳記。|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|擷取 managed 函式或變數的中繼資料語彙基元。|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|擷取函式簽章的參考。|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|擷取符號的類型識別項。|  
|[IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|擷取這個符號的編譯器專屬的型別值的陣列。|  
|[IDiaSymbol::get_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|擷取這個符號的編譯器專用的類型識別碼值的陣列。|  
|[IDiaSymbol::get_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|擷取 uav 位置。|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|擷取各種不同的使用者定義型別 (UDT)。|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|擷取表示使用者定義資料類型是否為未配置的旗標。|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|擷取的未裝飾的名稱是 c + + 裝飾，或連結，名稱。|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|延伸模組的`get_undecoratedName`擷取的延伸模組欄位值為基礎的未裝飾的名稱的方法。|  
|[IDiaSymbol::get_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|擷取原始 （未修改） 類型的識別碼。|  
|[IDiaSymbol::get_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|擷取 FORTRAN 陣列維度的上限。|  
|[IDiaSymbol::get_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|擷取符號識別碼，FORTRAN 陣列維度的上限。|  
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|擷取常數的值。|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|擷取指出是否為虛擬函式的旗標。|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|擷取位置的虛擬位址 (VA)。|  
|[IDiaSymbol::get_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|擷取表示使用者定義資料類型是否為虛擬基底類別的旗標。|  
|[IDiaSymbol::get_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|擷取虛擬基底位移資料表的索引。|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|擷取虛擬函式的虛擬函式資料表中的位移。|  
|[IDiaSymbol::get_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|擷取虛擬基底指標的位移。|  
|[IDiaSymbol::get_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|擷取虛擬基底資料表指標的類型。|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|擷取的符號介面之類型的使用者定義類型的虛擬資料表。|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|擷取符號的虛擬資料表圖形識別項。|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|擷取表示是否在使用者定義資料類型暫時性的旗標。|  
  
## <a name="remarks"></a>備註  
  
## <a name="notes-for-callers"></a>呼叫端資訊  
 取得此介面，藉由呼叫下列方法之一：  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## <a name="example"></a>範例  
 這個範例示範如何顯示在指定的相對虛擬位址的函式的區域變數。 它也會顯示不同類型的符號與彼此如何相關。  
  
> [!NOTE]
>  `CDiaBSTR` 是一個類別，包裝`BSTR`並自動處理當具現化超出範圍時釋出的字串。  
  
```C++  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## <a name="requirements"></a>需求  
 `Header:` dia2.h  
  
 程式庫： diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>另請參閱  
 [介面 （偵錯介面存取 SDK）](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [符號類型的類別階層架構](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [符號和符號標記](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [編譯模組](../../debugger/debug-interface-access/compiland.md)