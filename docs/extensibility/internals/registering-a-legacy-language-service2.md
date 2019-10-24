---
title: 註冊舊版語言 Service2 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e1cb2d8193d0ffa6285357634b8bcab549ecbf6
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724739"
---
# <a name="registering-a-legacy-language-service"></a>註冊舊版語言服務
下列各節提供 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 中可用之各種語言服務選項的登錄專案清單。

 在下列登錄專案清單中， *VS Reg Root*等於 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\*X*，其中*X. y*是 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 版本號碼。

## <a name="registry-entries-for-language-service-options"></a>語言服務選項的登錄專案
 *VS Reg Root*\Languages\Language Services \\*語言名稱*金鑰可以包含下列值。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|*\<GUID >*|語言服務的 GUID。|
|LangResID|REG_DWORD|0x0-0xffff|語言的當地語系化文字名稱的字串資源識別碼（ResID）。|
|封裝|REG_SZ|*\<GUID >*|VSPackage 的 GUID。|
|ShowCompletion|REG_DWORD|0-1|指定是否啟用 [**選項**] 對話方塊中的**語句完成**選項。|
|ShowSmartIndent|REG_DWORD|0-1|指定是否啟用 [**選項**] 對話方塊中選取 [**智慧**縮排] 的選項。|
|RequestStockColors|REG_DWORD|0-1|指定自訂或預設色彩是否用於色彩關鍵字。|
|ShowHotURLs|REG_DWORD|0-1|指定使用者是否可以按一下 [Url]。|
|預設為非熱門 Url|REG_DWORD|0-1|在 [**選項**] 對話方塊中，指定 [**啟用單鍵 URL] 流覽**選項的初始設定。|
|DefaultToInsertSpaces|REG_DWORD|0-1|指定語言服務是否有 [插入空格] 做為預設的索引標籤選項。|
|ShowDropdownBarOption|REG_DWORD|0-1|啟用或停用 [**選項**] 對話方塊中顯示或隱藏**巡覽列**的 [**導覽**列] 選項。|
|僅限單一程式碼視窗|REG_DWORD|0-1|在語言服務的 [**視窗]** 功能表中，啟用或停用 [**新增視窗]** 選項。|
|EnableAdvancedMembersOption|REG_DWORD|0-1|啟用或停用 [**隱藏 Advanced 成員**] 的 [**選項**] 對話方塊設定。|
|支援 CF_HTML|REG_DWORD|0-1|指定編輯器是否允許複製和貼上 HTML 資料。|
|EnableLineNumbersOption|REG_DWORD|0-1|指定是否為語言服務啟用 [**選項**] 對話方塊中的 [**行號**] 選項。|
|HideAdvancedMembersByDefault|REG_DWORD|0-1|指定是否在完成清單中隱藏 advanced 成員（例如私用欄位）。|
|ShowBraceCompletion|REG_DWORD|0-1|指定是否啟用 [**選項**] 對話方塊中的**大括弧自動完成**選項。|

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

## <a name="registry-entries-for-debugger-languages-options"></a>偵錯工具語言選項的登錄專案
 *VS Reg Root*\Languages\Language Services \\*語言名稱 \Debugger Language*\\*GUID*\ key 可以包含下列值。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|文字|預設值可以用來記錄語言的名稱。 此索引鍵的名稱是運算式評估工具的 GUID，其在 *\<VS Reg Root >* \AD7Metrics\Expression 評估工具中具有對應的專案。|

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

## <a name="registry-entries-for-editor-tools-options"></a>編輯器工具選項的登錄專案
 您可以在 [屬性頁] 和 [屬性] 節點的 EditorToolsOptions 機碼底下加入登錄機碼。 這些索引鍵及其值會識別 [**選項**] 對話方塊（位於 [**工具**] 功能表上）中用來設定語言服務的屬性頁。 在下列範例中，[*頁面名稱*] 是屬性頁的名稱，而 [*節點名稱*] 是 [**選項**] 對話方塊上樹狀目錄中的節點名稱。 您必須分別指定頁面輸入和節點專案。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|ResID|此選項頁面的當地語系化顯示名稱。 名稱可以是常值文字或 # `nnn`，其中 `nnn` 是指定 VSPackage 之附屬 DLL 中的字串資源識別碼。|
|封裝|REG_SZ|*GUID*|執行此 [選項] 頁面的 VSPackage GUID。|
|頁面|REG_SZ|*GUID*|藉由呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 方法，從 VSPackage 要求的屬性頁 GUID。 如果此登錄專案不存在，則登錄機碼會描述節點，而不是頁面。|

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

## <a name="registry-entries-for-file-name-extension-options"></a>檔案名擴充功能選項的登錄專案
 副檔名的專案應該包含前置句點，例如 "myext"。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|*GUID*|此副檔名類型之預設語言服務的服務 GUID。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>編輯器選項的登錄專案
 *VS Reg Root*\Editors key 可以包含下列值：

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|""|未使用您可以將您的名稱放在這裡以取得檔。|
|DefaultToolboxTab|REG_SZ|""|[工具箱] 索引標籤的名稱，以在編輯器作用中時設為預設值。|
|DisplayName|REG_SZ|ResID|要在 [**開啟方式**] 對話方塊中顯示的名稱。 名稱是字串資源識別碼或標準格式的名稱。|
|ExcludeDefTextEditor|REG_DWORD|0-1|用於 [**開啟方式**] 功能表命令。 如果您不想要在特定檔案類型的可用編輯器清單中列出預設文字編輯器，請將此值設定為1。|
|LinkedEditorGUID|REG_SZ|*\<GUID >*|用於任何可開啟具有字碼頁支援之檔案的語言服務。 例如，當您使用 [**開啟**檔案] 命令來開啟 .txt 檔案時，會提供選項，讓您使用原始程式碼編輯器搭配和不進行編碼。<br /><br /> 子機碼的名稱中指定的 GUID 是用於字碼頁編輯器 factory;此特定登錄專案中指定的連結 GUID 適用于一般編輯器 factory。 此專案的目的是如果 IDE 不會使用預設編輯器來開啟檔案，IDE 會嘗試使用清單中的下一個編輯器。 下一個編輯器不應該是字碼頁編輯器 factory，因為此編輯器 factory 基本上與失敗的編輯器 factory 相同。|
|封裝|REG_SZ|*\<GUID >*|VSPackage 顯示名稱的 ResID 的 GUID。|

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

## <a name="registry-entries-for-logical-view-options"></a>邏輯視圖選項的登錄專案
 *VS Reg 根*\Editors\\*編輯器 GUI >* \LogicalViews 金鑰可以包含下列值。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ||未使用。|
|*\<GUID >*|REG_SZ|""|支援之邏輯視圖的索引鍵。 您可以視需要擁有許多這些。 登錄專案的名稱是重要的，而不是值，它一律是空字串。|

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

## <a name="registry-entries-for-editor-extension-options"></a>編輯器延伸模組選項的登錄專案
 *VS Reg 根*\Editors\\*Editor GUID*\Extensions 金鑰可以包含下列值。 副檔名不包含前置句點。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ||未使用。|
|*\<ext >*|REG_DWORD|0-0xffffffff|擴充功能的相對優先順序。 如果兩個以上的語言共用相同的副檔名，則會選擇較高優先順序的語言。|

 此外，目前使用者的編輯器預設選取專案是儲存在 HKEY_Current_User\Software\Microsoft\VisualStudio\\*X. Y*\Default 編輯器\\*ext*中。所選取語言服務的 GUID 在自訂專案中。 這會優先使用目前的使用者。

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>Managed 封裝架構語言服務選項的登錄專案
 下列登錄專案是 managed package framework （MPF）語言服務類別的特定專案。 這些登錄專案指出語言服務中各種 IntelliSense 功能和其他先進編輯功能的支援。

 這些登錄專案可透過 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 類別來存取。

|[屬性]|輸入|Range|描述|
|----------|----------|-----------|-----------------|
|CodeSense|REG_DWORD|0-1|IntelliSense 作業的支援。|
|MatchBraces|REG_DWORD|0-1|支援成對的語言組，例如大括弧、括弧和方括弧。|
|QuickInfo|REG_DWORD|0-1|IntelliSense 快速諮詢作業的支援。|
|ShowMatchingBrace|REG_DWORD|0-1|支援在狀態列中顯示相符的語言組。|
|MatchBracesAtCaret|REG_DWORD|0-1|支援顯示相符的語言組，通常是透過反白顯示這兩個元素。|
|MaxErrorMessages|REG_DWORD|0-n|可以在**錯誤清單**視窗中顯示的錯誤數目上限。|
|CodeSenseDelay|REG_DWORD|0-n|起始 IntelliSense 作業的任何背景剖析之前，所要延遲的毫秒數。|
|EnableAsyncCompletion|REG_DWORD|0-1|支援背景剖析。|
|EnableCommenting|REG_DWORD|0-1|支援將選取的文字區塊批註化，同時也表示支援取消批註選取的文字。|
|EnableFormatSelection|REG_DWORD|0-1|支援格式化文字（例如自動縮排或調整大括弧的位置）。|
|AutoOutlining|REG_DWORD|0-1|支援大綱（可折迭的區域）。|
|MaxRegions|REG_DWORD|0-n|每個檔案的隱藏區域數目上限。|

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

## <a name="see-also"></a>請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)