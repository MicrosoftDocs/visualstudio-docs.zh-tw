---
title: 進階建置設定對話方塊 (C#) | Microsoft Docs
ms.custom: ''
ms.date: 06/20/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 406b25a3130b69b94486e866479e819dc68e70a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="advanced-build-settings-dialog-box-c"></a>進階建置設定對話方塊 (C#)

使用 [專案設計工具] 的 [進階建置設定] 對話方塊，以指定專案的進階組建組態屬性。 此對話方塊只適用於 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案。

## <a name="general"></a>一般

 下列選項可讓您設定一般進階設定。

 **語言版本**：指定要使用的語言版本。 每個版本的功能集都不同，因此這個選項可用來強制編譯器只允許已實作功能的子集，或只啟用與現有標準相容的功能。 此設定具有下列選項：

 - **default**

   以目前版本為目標。

- **ISO-1** 和 **ISO-2**

  分別以 ISO-1 和 ISO-2 標準功能為目標。

- **C# [版本號碼]**

 以 C# 的特定版本為目標。 如需詳細資訊，請參閱 [/langversion (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)。


 **內部編譯器錯誤報告**：指定是否要向 Microsoft 報告編譯器錯誤。 如果設定為 [提示]\(預設值)，您會在發生內部編譯器錯誤時收到提示，讓您選擇以電子方式將錯誤報告傳送給 Microsoft。 如果設定為 [傳送]，則會自動傳送錯誤報告。 如果設定為 [佇列]，則會將錯誤報告排入佇列。 如果設定為 [無]，則會以編譯器的文字輸出報告錯誤。 如需詳細資訊，請參閱 [/errorreport (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)。

 **檢查算術溢位/反向溢位**：指定不在 [checked](/dotnet/csharp/language-reference/keywords/checked) 或 [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) 關鍵字範圍內，且會產生超出該資料類型範圍之值的整數算術運算式，是否會導致執行階段例外狀況。 如需詳細資訊，請參閱 [/checked (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option)。

 **不要參考 mscorlib.dll**：指定是否要將 mscorlib.dll 匯入您的程式，並定義整個 <xref:System> 命名空間。 如果您想要定義或建立自己的 <xref:System> 命名空間和物件，請核取此方塊。 如需詳細資訊，請參閱 [/nostdlib (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option)。

## <a name="output"></a>輸出

 下列選項可讓您指定進階輸出選項。

 **偵錯資訊**：指定編譯器所產生的偵錯資訊類型。 如需如何設定應用程式效能偵錯的資訊，請參閱[使映像偵錯更容易](http://msdn.microsoft.com/Library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3)。 此設定具有下列選項：

- **none**

  指定不會產生任何偵錯資訊。

- **full**

  允許將偵錯工具附加至執行中的程式。

- **pdbonly**

  讓原始程式碼在偵錯工具中啟動程式時進行偵錯，但只有在將執行中的程式附加到偵錯工具時，才會顯示組譯工具。
- **portable**

  產生 .PDB 檔案，這是非平台特定可攜式符號檔，可將主要可執行檔中項目的資訊和其產生方式提供給其他工具 (特別是偵錯工具)。 如需詳細資訊，請參閱 [Portable PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (可攜式 PDB)。

- **embedded**

  在組件中內嵌可攜式符號資訊。 不會產生任何外部 .PDB 檔案。

如需詳細資訊，請參閱 [/debug (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)。

**檔案對齊**：指定輸出檔案中的區段大小。 有效值為 **512**、**1024**、**2048**、**4096** 和 **8192**。 這些值是以位元組為單位。 每個區段將會對齊界限，而這個界限就是此值的倍數，會影響輸出檔的大小。 如需詳細資訊，請參閱 [/filealign (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option)。

**程式庫基底位址**：指定載入 DLL 時慣用的基底位址。 DLL 的預設基底位址是由 [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] 通用語言執行平台所設定。 如需詳細資訊，請參閱 [/baseaddress (C# 編譯器選項)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option)。

## <a name="see-also"></a>請參閱

 [C# 編譯器選項](/dotnet/csharp/language-reference/compiler-options/index) [專案設計工具、建置頁面 (C#)](../../ide/reference/build-page-project-designer-csharp.md)
