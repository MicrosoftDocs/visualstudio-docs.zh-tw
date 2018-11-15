---
title: 進階編譯器設定對話方塊 (Visual Basic) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedCompile
helpviewer_keywords:
- Advanced Compiler Settings dialog box
ms.assetid: 1f81133a-293f-4dba-bc1c-8baafb01d857
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd910b0e0295ca12807b96af189032ffec766429
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949821"
---
# <a name="advanced-compiler-settings-dialog-box-visual-basic"></a>進階編譯器設定對話方塊 (Visual Basic)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
使用 [專案設計工具] 的 [進階編譯器設定] 對話方塊，以指定專案的進階組建組態屬性。 此對話方塊只適用於 Visual Basic 專案。  
  
### <a name="to-access-this-dialog-box"></a>若要存取此對話方塊  
  
1. 在方案總管中，選擇專案節點 (而不是 [方案] 節點)。  
  
2. 在 [專案] 功能表上，按一下 [屬性]。 [專案設計工具] 出現時，請按一下 [編譯] 索引標籤。  
  
3. 在[專案設計工具、編譯頁 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)，選取 [設定] 和 [平台]。 在簡化的組建設定中，不會顯示 [設定] 和 [平台] 清單。 如需詳細資訊，請參閱[偵錯和發行專案組態](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e)。  
  
4. 按一下 [進階編譯選項]。  
  
   [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="optimizations"></a>最佳化  
 下列選項指定的最佳化，在某些情況下可能會讓程式檔較小、程式執行速度更快，或是加速建置程序。  
  
 **移除整數的溢位檢查**  
 根據預設，會清除此核取方塊，以啟用整數溢位檢查。 選取此核取方塊，可移除整數溢位檢查。 如果您選取此核取方塊，整數計算可能會比較快。 不過，如果您移除溢位檢查且資料型別容量溢位，則可能會儲存不正確的結果而不引發錯誤。  
  
 如果檢查溢位條件且整數運算發生溢位，則會擲回 <xref:System.OverflowException> 例外狀況。 如果不檢查溢位條件，整數運算溢位並不會擲回例外狀況。  
  
 **啟用最佳化**  
 根據預設，會清除此核取方塊，以停用編譯器最佳化。 選取此核取方塊，可啟用編譯器最佳化。 編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。 不過，因為最佳化導致輸出檔中的程式碼重新排列，編譯器最佳化可能會使偵錯困難。  
  
 **DLL 基底位址**  
 此文字方塊會以十六進位格式顯示預設的 DLL 基底位址。 在類別庫和控制項程式庫專案中，您可以使用這個文字方塊來指定在建立 DLL 時要使用的基底位址。  
  
 **產生偵錯資訊**  
 從清單中選取 [無]、[完整] 或 [僅限 pdb]。 [無] 會指定不產生任何偵錯資訊。 [完整] 指定要產生完整的偵錯資訊，而 [僅限 pdb] 則指定只要產生 PDB 偵錯資訊。 根據預設，這個選項會設為 [完整]。  
  
## <a name="compilation-constants"></a>編譯常數  
 條件式編譯的常數有一個類似在原始程式檔中使用 [#Const](http://msdn.microsoft.com/library/707669e5-23f9-4f17-8622-a0d534429386) 前置處理器指示詞的效果，只除了定義的常數是公開的，且適用於專案中的所有檔案。 您可以使用條件式編譯常數，並搭配 [#If...Then...#Else](http://msdn.microsoft.com/library/10bba104-e3fd-451b-b672-faa472530502) 指示詞有條件地編譯原始程式檔。 請參閱[條件式編譯](http://msdn.microsoft.com/library/9c35e55e-7eee-44fb-a586-dad1f1884848)。  
  
 **定義 DEBUG 常數**  
 根據預設，會選取此核取方塊，指定將設定 DEBUG 常數。  
  
 **定義 TRACE 常數**  
 根據預設，會選取此核取方塊，指定將設定 TRACE 常數。  
  
 **自訂常數**  
 在此文字方塊中為您的應用程式輸入任何自訂常數。 項目應該使用這種形式以逗號分隔：**Name1="Value1",Name2="Value2",Name3="Value3"**。  
  
## <a name="other-settings"></a>其他設定  
 **產生序列化組件**  
 此設定指定編譯器是否會建立 XML 序列化組件。 如果您已在程式碼中使用該類別將類型序列化，則序列化組件可提升 <xref:System.Xml.Serialization.XmlSerializer> 的啟動效能。 此選項預設為 [自動]，指定只有您已在程式碼中使用 <xref:System.Xml.Serialization.XmlSerializer> 將類型編碼為 XML 時，才會產生序列化組件。 [關閉] 指定不論您的程式碼是否使用 <xref:System.Xml.Serialization.XmlSerializer>，永遠不會產生序列化組件。 **On** 指定永遠會產生序列化組件。 序列化組件將命名為 `TypeName`.XmlSerializers.dll。  
  
## <a name="see-also"></a>另請參閱  
 [專案設計工具、編譯頁面 (Visual Basic)](../../ide/reference/compile-page-project-designer-visual-basic.md)



