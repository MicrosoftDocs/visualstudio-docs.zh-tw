---
title: 註冊舊版語言服務 2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 77a7138e436002a0fda4e9ab72222821d2c9809e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909036"
---
# <a name="registering-a-legacy-language-service"></a>註冊舊版語言服務
下列各節提供的登錄項目清單的各種語言中可用的服務選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

 登錄項目下, 面*VS Reg 根*等於 hkey_local_machine\software\microsoft\visualstudio \\*X.Y*，其中*X.Y*是[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本號碼。

## <a name="registry-entries-for-language-service-options"></a>語言服務選項的登錄項目
 *VS Reg 根*\Languages\Language Services\\*語言名稱*索引鍵可以包含下列值。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|*\<GUID>*|語言服務的 GUID。|
|LangResID|REG_DWORD|0x0-0xffff|字串資源識別項 (ResID) 語言的當地語系化的文字名稱。|
|套件|REG_SZ|*\<GUID>*|VSPackage 的 GUID。|
|ShowCompletion|REG_DWORD|0-1|指定是否**陳述式完成**中的選項**選項**對話方塊會啟用。|
|ShowSmartIndent|REG_DWORD|0-1|指定是否可以選取**智慧型**中的縮排**選項** 對話方塊中已啟用。|
|RequestStockColors|REG_DWORD|0-1|指定是否為自訂或預設的色彩來將色彩關鍵字。|
|ShowHotURLs|REG_DWORD|0-1|指定使用者是否可以按一下 Url。|
|預設為非經常性存取的 Url|REG_DWORD|0-1|指定的初始設定**啟用按一下方式的 URL 導覽**選項**選項** 對話方塊。|
|DefaultToInsertSpaces|REG_DWORD|0-1|指定語言服務是否有 「 插入空格 」 做為其預設值 索引標籤選項。|
|ShowDropdownBarOption|REG_DWORD|0-1|啟用或停用**瀏覽列**選項**選項**可顯示或隱藏對話方塊**導覽列**。|
|僅適用於單一程式碼視窗|REG_DWORD|0-1|啟用或停用**開新視窗**中選擇**視窗**語言服務的功能表。|
|EnableAdvancedMembersOption|REG_DWORD|0-1|啟用或停用**選項** 對話方塊的設定為**隱藏進階成員**。|
|支援 CF_HTML|REG_DWORD|0-1|指定編輯器是否啟用複製並貼上的 HTML 資料。|
|EnableLineNumbersOption|REG_DWORD|0-1|指定是否**行號**中的選項**選項**對話方塊都可使用的語言服務。|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|指定完成清單中是否會隱藏進階的成員，例如私用欄位。|
|ShowBraceCompletion|REG_DWORD|0-1|指定是否**完成的括號**選項**選項** 對話方塊中已啟用。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        (Default)             = reg_sz:{B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
        LangResID             = reg_dword:0x00000000
        Package               = reg_sz:{8C2EA640-ABC1-11D0-9D62-00C04FD9DFD9}
        ShowCompletion        = reg_dword:0x00000001
        ShowSmartIndent       = reg_dword:0x00000001
        ShowDropdownBarOption = reg_dword:0x00000001
```

## <a name="registry-entries-for-debugger-languages-options"></a>如需偵錯工具的語言選項的登錄項目
 *VS Reg 根*\Languages\Language Services\\*語言名稱*\Debugger 語言\\*GUID*\ 索引鍵可以包含下列項目值。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|文字|預設值可以用於文件的語言名稱。 此索引鍵的名稱會有對應的項目中的運算式評估工具的 GUID  *\<VS Reg 根 >* \AD7Metrics\Expression 評估工具。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      C/C++\
        Debugger Languages\
          {3A12D0B7-C26C-11D0-B442-00A0244A1DD2}\
            (Default) = reg_sz:C++
```

## <a name="registry-entries-for-editor-tools-options"></a>編輯器工具選項的登錄項目
 您可以新增 EditorToolsOptions 機碼下的登錄機碼的屬性頁和屬性節點。 這些索引鍵和其值會識別中的屬性頁**選項** 對話方塊中 (在**工具**功能表)，用來設定語言服務。 在下列範例中，*頁面名稱*的 屬性 頁面中，名稱並*節點名稱*位於樹狀結構中節點的名稱**選項** 對話方塊。 必須個別指定，分頁項目和節點的項目。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|ResID|此選項 頁面的當地語系化的顯示名稱。 名稱可以是常值文字或 #`nnn`，其中`nnn`附屬 DLL 的指定 VSPackage 中的字串資源 id。|
|套件|REG_SZ|*GUID*|實作此選項頁面的 VSPackage 的 GUID。|
|頁面|REG_SZ|*GUID*|屬性頁的 GUID，藉由呼叫要求從 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。 如果此登錄項目不存在，將登錄機碼描述的節點，不是頁面。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      CSharp\
        EditorToolsOptions\
          Formatting\
            (Default) = reg_sz:#242
            Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
            General\
              (Default) = reg_sz:#255
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{3EB2CC0B-033E-4D75-B26A-B2362C25227E}
            Indentation\
              (Default) = reg_sz:#250
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{5E21D017-6D2A-4114-A1F1-C923F001CBBB}
            Newlines\
              (Default) = reg_sz:#253
              Package   = reg_sz:{A066E284-DCAB-11D2-B551-00C04F68D4DB}
              Page      = reg_sz:{607D8062-68D1-41E4-9A35-B5E7F14D0481}
```

## <a name="registry-entries-for-file-name-extension-options"></a>檔案名稱副檔名選項的登錄項目
 副檔名的項目應該包含前置的句點，例如".myext 」。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|*GUID*|此檔案名稱副檔名類型的預設語言服務的服務 GUID。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>編輯器選項的登錄項目
 *VS Reg 根*\Editors 索引鍵可以包含下列值：

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|""|未使用;您可以將您的名稱如文件。|
|DefaultToolboxTab|REG_SZ|""|若要將預設值，當編輯器是使用中的 [工具箱] 索引標籤的名稱。|
|DisplayName|REG_SZ|ResID|要在 [顯示名稱**開啟**] 對話方塊。 名稱為標準格式字串資源識別碼或名稱。|
|ExcludeDefTextEditor|REG_DWORD|0-1|用於**開啟**功能表命令。 如果您不要在清單中可用的編輯器清單的特定檔案類型的預設文字編輯器，設定此值為 1。|
|LinkedEditorGUID|REG_SZ|*\<GUID>*|用於可以使用字碼頁支援開啟檔案的任何語言服務。 例如，當您開啟.txt 檔案使用**開啟**命令時，會提供使用原始程式碼編輯器，包含或不含編碼的選項。<br /><br /> 指定名稱之子機碼的 GUID 是字碼頁編輯器 factory;這個特定的登錄項目中指定的連結的 GUID 是一般編輯器 factory。 這個項目的是，如果在 IDE 不會使用預設的編輯器開啟檔案，IDE 會嘗試使用清單中的下一個編輯器。 這個下一步 的編輯器應該不會是字碼頁編輯器 factory，因為此編輯器 factory 基本上是編輯器 factory 失敗的相同。|
|套件|REG_SZ|*\<GUID>*|顯示名稱的 ResID VSPackage 的 GUID。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      (Default)            = reg_sz:Html Editor with Encoding
      DefaultToolboxTab    = reg_sz:HTML
      DisplayName          = reg_sz:#20101
      LinkedEditorGUID     = reg_sz:{C76D83F8-A489-11D0-8195-00A0C91BBEE3}
      Package              = reg_sz:{1B437D20-F8FE-11D2-A6AE-00104BCC7269}
```

## <a name="registry-entries-for-logical-view-options"></a>如需邏輯檢視選項的登錄項目
 *VS Reg 根*\Editors\\*編輯器 GUI >* \LogicalViews 索引鍵可以包含下列值。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ||未使用。|
|*\<GUID>*|REG_SZ|""|若要支援的邏輯檢視的索引鍵。 視需要您可以有許多種。 登錄項目的名稱是什麼是重要的是，不是值，這一律是空字串。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      LogicalViews\
       (Default) = reg_sz:
       {7651a700-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a701-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a702-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
       {7651a703-06e5-11d1-8ebd-00a0c90f26ea} = reg_sz:
```

## <a name="registry-entries-for-editor-extension-options"></a>如需編輯器延伸模組選項的登錄項目
 *VS Reg 根*\Editors\\*編輯器 GUID*\Extensions 索引鍵可以包含下列值。 檔案名稱的副檔名不包括前置的句點。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ||未使用。|
|*\<ext>*|REG_DWORD|0-0xffffffff|擴充功能的相對優先權。 如果兩個或多個語言都共用同一個延伸模組，則會選擇較高優先順序的語言。|

 此外，目前使用者的預設選項，編輯器會儲存在 HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default 編輯器\\*ext*。選取的語言服務的 GUID 是自訂項目中。 這個選項的目前使用者的優先順序。

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\9.0\
  \Editors\
    {8281C572-2171-45AA-A642-7D8BC1662F1C}\
      Extensions\
       (Default) = reg_sz:
       *         = reg_dword:0x00000018
       html      = reg_dword:0x00000027
       shtm      = reg_dword:0x00000027
       shtml     = reg_dword:0x00000027
```

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Managed 的封裝架構語言服務選項的登錄項目
 下列的登錄項目特有的 managed 的封裝架構 (MPF) 語言服務類別。 這些登錄項目指示語言服務的各種 IntelliSense 功能和其他進階編輯功能的支援。

 這些登錄項目透過存取<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|IntelliSense 作業的支援。|
|MatchBraces|REG_DWORD|0-1|成對大括號、 括號和方括號等的語言支援。|
|QuickInfo|REG_DWORD|0-1|IntelliSense 快速諮詢作業的支援。|
|ShowMatchingBrace|REG_DWORD|0-1|支援在狀態列中顯示相符的語言組。|
|MatchBracesAtCaret|REG_DWORD|0-1|支援顯示語言配對，通常透過反白顯示兩個項目。|
|MaxErrorMessages|REG_DWORD|0-n|中可顯示的錯誤數目上限**錯誤清單**視窗。|
|CodeSenseDelay|REG_DWORD|0-n|若要延遲啟動任何背景剖析 IntelliSense 作業之前的毫秒數。|
|EnableAsyncCompletion|REG_DWORD|0-1|背景剖析支援。|
|EnableCommenting|REG_DWORD|0-1|支援標記為註解選取的文字區塊，也可能指定支援取消註解選取的文字。|
|EnableFormatSelection|REG_DWORD|0-1|格式化文字，例如自動縮排或調整大括號位置的支援。|
|AutoOutlining|REG_DWORD|0-1|大綱 （可以摺疊的區域） 的支援。|
|MaxRegions|REG_DWORD|0-n|隱藏的區域，每個檔案的數目上限。|

```
ExampleHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    Language Services\
      XML\
        (Default)             = reg_sz:{f6819a78-a205-47b5-be1c-675b3c7f0b8e}
        MatchBraces           = reg_dword:0x00000001
        QuickInfo             = reg_dword:0x00000001
        ShowMatchingBrace     = reg_dword:0x00000001
        MatchBracesAtCaret    = reg_dword:0x00000000
        MaxErrorMessages      = reg_dword:0x00000064
        CodeSenseDelay        = reg_dword:0x000001f4
        MaxRegions            = reg_dword:0x0000000a
```

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)