---
title: 進階編譯器設定對話方塊 (Visual Basic)
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9ebc2da5e71dbdee13df4cf658f3681804879f58
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596927"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>進階編譯器設定對話方塊 (Visual Basic)

使用 [專案設計工具]**** 的 [進階編譯器設定]**** 對話方塊，以指定專案的進階組建組態屬性。 此對話方塊只適用於 Visual Basic 專案。

## <a name="to-access-this-dialog-box"></a>若要存取此對話方塊

1. 在方案總管**** 中，選擇專案節點 (而不是 [方案]**** 節點)。

2. 按一下 [專案]**** 功能表上的 [屬性]****。 當**專案設計器**出現時，按一下 **"編譯"** 選項卡。

3. 在[專案設計工具、編譯頁 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)，選取 [設定]**** 和 [平台]****。 在簡化的組建設定中，不會顯示 [設定]**** 和 [平台]**** 清單。 有關詳細資訊，請參閱[操作操作：設置調試和發佈配置](../../debugger/how-to-set-debug-and-release-configurations.md)。

4. 按一下 [進階編譯選項]****。

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

## <a name="optimizations"></a>最佳化

下列選項指定的最佳化，在某些情況下可能會讓程式檔較小、程式執行速度更快，或是加速建置程序。

**移除整數的溢位檢查**

預設會清除此核取方塊，以啟用整數溢位檢查。 選取此核取方塊，可移除整數溢位檢查。 如果您選取此核取方塊，整數計算可能會比較快。 不過，如果您移除溢位檢查且資料型別容量溢位，則可能會儲存不正確的結果而不引發錯誤。

如果檢查溢位條件且整數運算發生溢位，則會擲回 <xref:System.OverflowException> 例外狀況。 如果不檢查溢位條件，整數運算溢位並不會擲回例外狀況。

**啟用最佳化**

預設會清除此核取方塊，以停用編譯器最佳化。 選取此核取方塊，可啟用編譯器最佳化。 編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。 不過，因為最佳化導致輸出檔中的程式碼重新排列，編譯器最佳化可能會使偵錯困難。

 **DLL 基本位址**

此文字方塊會以十六進位格式顯示預設的 DLL 基底位址。 在類別庫和控制項程式庫專案中，您可以使用這個文字方塊來指定在建立 DLL 時要使用的基底位址。

 **產生偵錯資訊**

從清單中選取 [無]****、[完整]**** 或 [僅限 pdb]****。 [無]**** 會指定不產生任何偵錯資訊。 [完整]**** 指定要產生完整的偵錯資訊，而 [僅限 pdb]**** 則指定只應產生 PDB 偵錯資訊。 這個選項的預設值是 [完整]****。

## <a name="compilation-constants"></a>編譯常數

條件式編譯的常數有一個類似在原始程式檔中使用 [#Const](/dotnet/visual-basic/language-reference/directives/const-directive) 前置處理器指示詞的效果，只除了定義的常數是公開的，且適用於專案中的所有檔案。 您可以使用條件式編譯常數，並搭配 [#If...Then...#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives) 指示詞有條件地編譯原始程式檔。 請參閱[條件式編譯](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)。

 **定義 DEBUG 常數**

根據預設，會選取此核取方塊，指定將設定 DEBUG 常數。

 **定義 TRACE 常數**

根據預設，會選取此核取方塊，指定將設定 TRACE 常數。

 **自訂常數**

在此文字方塊中為您的應用程式輸入任何自訂常數。 項目應該使用這種形式以逗號分隔：**Name1="Value1",Name2="Value2",Name3="Value3"**。

## <a name="other-settings"></a>其他設定

**產生序列化組件**

此設定指定編譯器是否會建立 XML 序列化組件。 如果您已在程式碼中使用該類別將類型序列化，則序列化組件可提升 <xref:System.Xml.Serialization.XmlSerializer> 的啟動效能。 此選項的預設值為 **"自動**"。**Auto**指定僅在用於<xref:System.Xml.Serialization.XmlSerializer>將代碼中的類型編碼為 XML 時才生成序列化程式集。 [關閉]**** 指定不論您的程式碼是否使用 <xref:System.Xml.Serialization.XmlSerializer>，永遠不會產生序列化組件。 **On** 指定永遠會產生序列化組件。 序列化組件將命名為 `TypeName`.XmlSerializers.dll。

## <a name="see-also"></a>另請參閱

- [專案設計工具、編譯頁 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)
