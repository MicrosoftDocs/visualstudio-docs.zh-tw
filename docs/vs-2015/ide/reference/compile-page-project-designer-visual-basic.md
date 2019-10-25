---
title: 專案設計工具、編譯頁面 (Visual Basic) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesCompile
helpviewer_keywords:
- compilation, Visual Basic projects
- compilation, options [Visual Basic]
- compilers, Visual Basic options
- compilation, instructions [Visual Basic]
- compiler options, Visual Basic
- Project Designer, Compile page
- Compile page in Project Designer
ms.assetid: b2a80230-906e-4e85-b3e0-fcd9c40426e1
caps.latest.revision: 65
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db830e04388b7465c941e2fdf069b49f98951a1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660831"
---
# <a name="compile-page-project-designer-visual-basic"></a>專案設計工具、編譯頁 (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

請使用 [專案設計工具] 的 [編譯] 頁面來指定編譯指令。 您也可以在此頁面上指定進階編譯器選項及建置前或建置後事件。

 若要存取 [編譯] 頁面，請在方案總管中選擇專案節點 (而不是 [方案] 節點)。 然後選擇功能表列上的 [專案]、[屬性]。 [專案設計工具] 出現時，請按一下 [編譯] 索引標籤。

 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]

## <a name="configuration-and-platform"></a>組態和平台
 下列設定可讓您選取要顯示或修改的組態和平台。

> [!NOTE]
> 使用簡化的組建組態時，專案系統會決定要建置偵錯或發行版本。 因此，不會顯示 [組態] 和 [平台] 清單。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

 **組態** 指定要顯示或修改的組態設定。 設定是 [偵錯] (預設值)、[發行] 或 [所有組態]。 如需詳細資訊，請參閱[Debug 和 Release 專案](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)設定和 [How：建立及編輯組態](../../ide/how-to-create-and-edit-configurations.md)。

 **平台** 指定要顯示或修改的平台設定。 您可以指定 [任何 CPU] (預設值)、[x64] 或 [x86]。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

## <a name="compiler-configuration-options"></a>編譯器組建選項
 下列設定可讓您設定編譯器組態選項。

 **組建輸出路徑**指定此專案設定的輸出檔位置。 在此方塊中鍵入建置輸出的路徑，或者按一下 [瀏覽] 按鈕以選取路徑。 請注意，路徑是相對的；如果您輸入絕對路徑，它會儲存為相對路徑。 預設路徑為 bin\Debug\ 或 bin\Release\\。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

 使用簡化的組建組態時，專案系統會決定要建置偵錯或發行版本。 不論您指定的 [輸出路徑] 為何，[偵錯] 功能表 (F5) 中的 [建置] 命令都會將組建放在偵錯位置。 不過，[建置] 功能表中的 [建置] 命令卻會將其放在您指定的位置。 如需詳細資訊，請參閱[偵錯和發行專案組態](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)。

 **Option explicit**：指定是否允許變數隱含宣告。 選取 [On] 表示必須明確宣告變數。 如果變數未在使用前宣告，這會導致編譯器報告錯誤。 選取 [Off] 則表示允許隱含宣告變數。

 此設定對應於 [/optionexplicit](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) 編譯器選項。

 如果原始碼檔案包含 [Option Explicit 陳述式](https://msdn.microsoft.com/library/e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc)，則陳述式中的 `On` 或 `Off` 值會覆寫 [編譯] 頁面上的 [Option Explicit] 設定。

 當您建立新專案時，[編譯] 頁面上的 [Option Explicit] 設定會設定為 [選項] 對話方塊中的 [Option Explicit] 設定。 若要檢視或變更此對話方塊中的設定，請按一下 [工具] 功能表中的 [選項]。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 [VB 預設值] 中 [Option Explicit] 的初始預設設定是 [On]。

 將 [Option Explicit] 設定為 `Off` 通常不是好的做法。 一或多個位置中的變數名稱可能有拼字錯誤，這會在程式執行時造成非預期的結果。

 **Option strict**：指定是否強制執行嚴格的類型語意。 當 [Option Strict] 為 [On] 時，下列情況將造成編譯時期錯誤：

- 隱含縮小轉換

- 晚期繫結

- 導致 `Object` 類型的隱含類型化

  隱含資料類型轉換是縮小轉換時，會發生隱含縮小轉換錯誤。 如需詳細資訊，請參閱 [Option Strict 陳述式](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5)、[隱含和明確轉換](https://msdn.microsoft.com/library/77de1659-af8a-492c-967e-e7ef60ccce66)，以及[擴展和縮小轉換](https://msdn.microsoft.com/library/058c3152-6c28-4268-af44-2209e774f0bd)。

  當物件指派給宣告為 `Object` 類型之變數的屬性或方法時，該物件即為「晚期繫結」。 如需詳細資訊，請參閱 [Option Strict 陳述式](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5)與[早期和晚期繫結](https://msdn.microsoft.com/library/d6ff7f1e-b94f-4205-ab8d-5cfa91758724)。

  無法推斷宣告變數的適當類型時，會發生隱含物件類型錯誤，因此推斷類型為 `Object`。 這主要是發生在您使用 `Dim` 陳述式宣告變數而未使用 `As` 子句，並且 `Option Infer` 已設為關閉的時候。 如需詳細資訊，請參閱 [Option Strict 陳述式](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5)、[Option Infer 陳述式](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)，以及 [Visual Basic 語言規格](https://msdn.microsoft.com/library/42c30017-19d0-442e-87a2-850b66ddc3df)。

  [Option Strict] 設定對應於 [/optionstrict](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) 編譯器選項。

  如果原始碼檔案包含 [ Option Strict 陳述式](https://msdn.microsoft.com/library/5883e0c1-a920-4274-8e46-b0ff047eaee5)，則陳述式中的 `On` 或 `Off` 值會覆寫 [編譯] 頁面上的 [Option Strict] 設定。

  當您建立專案時，[編譯] 頁面上的 [Option Strict] 設定會設定為 [選項] 對話方塊中的 [Option Strict] 設定。 若要檢視或變更此對話方塊中的設定，請按一下 [工具] 功能表中的 [選項]。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 [VB 預設值] 中 [Option Strict] 的初始預設設定是 [Off]。

  **Option Strict 的個別警告。** [編譯] 頁面的 [警告組態] 區段中所包含的設定，對應於三個會在 `Option Strict` 設為 On 時導致編譯時期錯誤的狀況。 以下是這些設定：

- **隱含轉換**

- **晚期繫結，執行階段時呼叫可能失敗**

- **隱含類型，假設是 Object**

  當您將 [Option Strict] 設定為 [On] 時，這三個警告組態設定都會設定為 [錯誤]。 當您將 [Option Strict] 設定為 [Off] 時，所有三個設定都會設定為 [無]。

  您可以將每個警告組態個別變更為 [無]、[警告] 或 [錯誤]。 如果三個警告組態設定皆設為 [錯誤]，`On` 會出現在 `Option strict` 方塊中。 如果這三個都設定為 [無]，`Off` 會出現在此方塊中。 若為這些設定的其他任何組合，則會出現 [(自訂)]。

  **Option compare**：指定要使用的字串比較類型。 選取 [二進位]，可指示編譯器使用二進位、區分大小寫的字串比較。 選取 [文字]，則會使用依地區設定特性、不區分大小寫的文字字串比較。

  此設定對應於 [/optioncompare](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) 編譯器選項。

  如果原始碼檔案包含 [Option Compare 陳述式](https://msdn.microsoft.com/library/54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e)，則陳述式中的 `Binary` 或 `Text` 值會覆寫 [編譯] 頁面上的 [Option Compare] 設定。

  當您建立專案時，[編譯] 頁面上的 [Option Compare] 設定會設定為 [選項] 對話方塊中的 [Option Compare] 設定。 若要檢視或變更此對話方塊中的設定，請按一下 [工具] 功能表中的 [選項]。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 [VB 預設值] 中 [Option Compare] 的初始預設設定是 [二進位]。

  **Option infer**：指定是否允許變數宣告中的區域型別推斷。 選取 [On] 表示允許使用區域型別推斷。 選取 [Off] 則表示封鎖區域型別推斷。

  此設定對應於 [/optioninfer](https://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed) 編譯器選項。

  如果原始碼檔案包含 [Option Infer 陳述式](https://msdn.microsoft.com/library/4ad3e6e9-8f5b-4209-a248-de22ef6e4652)，則陳述式中的 `On` 或 `Off` 值會覆寫 [編譯] 頁面上的 [Option Infer] 設定。

  當您建立專案時，[編譯] 頁面上的 [Option Infer] 設定會設定為 [選項] 對話方塊中的 [Option Infer] 設定。 若要檢視或變更此對話方塊中的設定，請按一下 [工具] 功能表中的 [選項]。 在 [選項] 對話方塊中，展開 [專案和方案]，然後按一下 [VB 預設值]。 [VB 預設值] 中 [Option Infer] 的初始預設設定是 [On]。

  **目標 CPU**：指定輸出檔案設為目標的處理器。 針對任何 32 位元 Intel 相容處理器指定 [x86]，針對任何 64 位元 Intel 相容處理器指定 [x64]，針對任何 ARM 處理器指定 [ARM]，或指定 [任何 CPU] 來指定可接受任何處理器。 [任何 CPU] 是新專案的預設值，因為這可讓應用程式在數目最多的硬體類型上執行。

  如需詳細資訊，請參閱 [/platform (Visual Basic)](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1)。

  **偏好 32 位元** 若選取 [Prefer32-bit] \(偏好 32 位元\) 核取方塊，應用程式將在 32 位元與 64 位元的 Windows 上作為 32 位元應用程式執行。 否則，應用程式會在 32 位元版本的 Windows 上當作 32 位元應用程式執行，並在 64 位元版本的 Windows 上當作 64 位元應用程式執行。

  執行 64 位元應用程式會加倍指標大小，它可能會造成與專用於 32 位元程式庫的相容性問題。 只有在其執行速度明顥加快或需要超過 4 GB 的記憶體時，才需要執行 64 位元等應用程式。

  只有在下列所有條件都成立時，才能使用此核取方塊：

- 在 [編譯] 頁面上，[目標 CPU] 清單會設為 [任何 CPU]。

- 在 [應用程式] 頁面上，[應用程式類型] 清單指定專案是應用程式。

- 在 [應用程式] 頁面上，[目標 Framework] 清單指定 .NET Framework 4.5。

  **警告組態**：此表格會列出組建條件及各項條件所對應的 [無]、[警告] 或 [錯誤] 通知層級。

  根據預設，所有的編譯器警告都會在編譯期間新增至工作清單中。 選取 [停用所有警告]，可指示編譯器不要發出警告或錯誤。 如果您要編譯器將警告視為必須修正的錯誤，請選取 [將所有警告視為錯誤]。

  **停用所有警告**：指定是否允許編譯器發出通知，如本文件稍早的 [條件和通知] 表格中所述。 根據預設，會清除此核取方塊。 選取此核取方塊，可指示編譯器不要發出警告或錯誤。

  此設定對應於 [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) 編譯器選項。

  **將所有警告視為錯誤**：指定如何看待警告。 此核取方塊預設為清除，也就是所有警告通知仍然設定為 [警告]。 請選取此核取方塊，將所有警告通知變更為 [錯誤]。

  只有在清除 [停用所有警告] 的情況下，才能使用此選項。

  **產生 XML 文件檔案**：指定是否要產生文件資訊。 此核取方塊預設為選取，可指示編譯器產生文件資訊並將其包含在 XML 檔案中。 清除此核取方塊，則會指示編譯器不要建立文件。

  此設定對應於 [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65) 編譯器選項。

  **註冊 COM Interop**：指定受控應用程式是否將公開 COM 物件 (COM 可呼叫包裝函式)，讓 COM 物件與應用程式互動。

  此核取方塊預設為清除，也就是指定應用程式不允許 COM Interop。 請選取此核取方塊來允許使用 COM Interop。

  此選項不適用於 [Windows 應用程式] 或 [主控台應用程式] 專案。

  **建置事件**：按一下此按鈕可存取 [建置事件] 對話方塊。 請使用此對話方塊來指定專案的建置前和建置後組態指令。 此對話方塊只適用於 Visual Basic 專案。 如需詳細資訊，請參閱[建置事件對話方塊 (Visual Basic)](../../ide/reference/build-events-dialog-box-visual-basic.md)。

  **進階編譯選項**：按一下此按鈕可存取 [進階編譯器設定] 對話方塊。 請使用 [進階編譯器設定] 對話方塊來指定專案的進階建置組態屬性。 此對話方塊只適用於 Visual Basic 專案。 如需詳細資訊，請參閱[進階編譯器設定對話方塊 (Visual Basic)](../../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)。

## <a name="see-also"></a>另請參閱
 [Debug 和 Release 專案](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)設定[管理編譯屬性](https://msdn.microsoft.com/94308881-f10f-4caf-a729-f1028e596a2c)[How：指定組建事件（Visual Basic） ](../../ide/how-to-specify-build-events-visual-basic.md) [Visual Basic 命令列編譯器](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)[How 至：建立及編輯組態](../../ide/how-to-create-and-edit-configurations.md)
