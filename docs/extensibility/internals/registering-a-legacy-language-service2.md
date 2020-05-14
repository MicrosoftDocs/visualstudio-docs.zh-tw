---
title: 註冊傳統語言服務2 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d9d13f301f6c04c0f7b14cc8c685f08b072ef84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705893"
---
# <a name="registering-a-legacy-language-service"></a>註冊舊版語言服務
以下各節提供了[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]中 提供的各種語言服務選項的註冊表項清單。

 在下面的註冊表項清單中 *,VS Reg Root*\\等於HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio*X.Y*,其中*X.Y*是[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本號。

## <a name="registry-entries-for-language-service-options"></a>語言服務選項的註冊表項
 *VS Reg 根*\\\語言\ 語言服務*語言名稱*鍵可以包含以下值。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|*\<GUID>*|語言服務的 GUID。|
|朗雷斯ID|REG_DWORD|0x0-0xff|語言的本地化文字名稱的字串資源標識碼 (ResID)。|
|Package|REG_SZ|*\<GUID>*|VS 包的 GUID。|
|顯示完成|REG_DWORD|0-1|指定是否啟用了「**選項**」對話框中的 **「語句完成**」選項。|
|顯示智慧縮排|REG_DWORD|0-1|指定是否啟用了在 **「選項**」對話框中選擇 **「智慧**縮進」的選項。|
|要求庫存顏色|REG_DWORD|0-1|指定自訂顏色還是預設顏色用於為關鍵字著色。|
|顯示 HotURL|REG_DWORD|0-1|指定使用者是否可以按下網址。|
|預設為非熱網址|REG_DWORD|0-1|在**選項「 對話**框中指定啟用 **」啟用一鍵網址導航**「選項的初始設定。|
|預設插入空白|REG_DWORD|0-1|指定語言服務是否具有「插入空格」作為其預設選項卡選項。|
|顯示下方放置列選項|REG_DWORD|0-1|開啟或關閉**選項「** 對話框中的**導航列**」 選項, 此對話框顯示或隱藏**導覽列**。|
|只限單代碼視窗|REG_DWORD|0-1|在**語言服務的「視窗」** 選單中啟用或禁用 **「新建視窗**」選項。|
|開啟進階會員選項|REG_DWORD|0-1|啟用或停用「**隱藏進階成員」****的選項**對話框設定。|
|支援CF_HTML|REG_DWORD|0-1|指定編輯器是否啟用 HTML 資料的複製和貼上。|
|開啟線編號選項|REG_DWORD|0-1|指定是否為語言服務啟用「**對話**框中的 **」行號選項**。|
|隱藏進階成員按預設值|REG_DWORD|0-1|指定進階成員(如專用欄位)是否隱藏在完成清單中。|
|顯示佈雷斯完成|REG_DWORD|0-1|指定是否啟用**選項**「對話框中的 **」大括弧完成**選項。|

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

## <a name="registry-entries-for-debugger-languages-options"></a>除錯器語言選項的註冊表項
 *VS Reg 根*\\[語言] 語言服務*語言名稱*\\[調試器語言*GUID*] 鍵可以包含以下值。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|text|預設值可用於記錄語言的名稱。 此鍵的名稱是表達式賦值器的 GUID,該運算式賦值器*\<在 VS Reg 根>*[AD7Metrics_運算式賦值器》中具有相應的條目。|

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

## <a name="registry-entries-for-editor-tools-options"></a>編輯工具選項的註冊表項
 您可以在屬性頁和屬性節點的 EditorToolsOptions 鍵下添加註冊表項。 這些鍵及其值識別用於設定語言服務**的選項**對話方塊(**在"工具**"選單上)中的屬性頁。 在下面的範例中,*頁面名稱*是屬性頁的名稱,*節點名稱*是 **「選項」** 對話框中樹中的節點的名稱。 頁面項目和節點項目必須單獨指定。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|渣 油|此選項頁的本地化顯示名稱。 名稱可以是文字文本,或`nnn`*`nnn`,其中 是指定 VSPackage 的附屬 DLL 中的字串資源 ID。|
|Package|REG_SZ|*Guid*|實現此選項頁的 VS 包的 GUID。|
|頁面|REG_SZ|*Guid*|屬性頁的 GUID 通過<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>調用 方法從 VSPackage 請求。 如果不存在此註冊表項,註冊表項將描述節點,而不是頁面。|

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

## <a name="registry-entries-for-file-name-extension-options"></a>檔案名副檔選項的註冊表項
 檔副檔名的條目應包括前導期間,例如".myext"。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|*Guid*|此檔名副檔名類型的預設語言服務服務 GUID。|

### <a name="example"></a>範例

```
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\
  Languages\
    File Extensions\
      .cpp\
        (Default) = {B2F072B0-ABC1-11D0-9D62-00C04FD9DFD9}
```

## <a name="registry-entries-for-editor-options"></a>編輯器選項的註冊表項
 *VS Reg 根*\編輯器金鑰可以包含以下值:

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ|""|未使用;您可以將您的姓名放在此處進行文件記錄。|
|DefaultToolboxTab|REG_SZ|""|工具箱選項卡的名稱,用於在編輯器處於活動狀態時進行預設值。|
|DisplayName|REG_SZ|渣 油|要在 **「打開使用」** 對話框中顯示的名稱。 名稱是字串資源 ID 或標準格式的名稱。|
|排除文字編輯器|REG_DWORD|0-1|用於**打開"隨"** 菜單命令。 如果不想在特定檔案類型的可用編輯器列表中列出預設文本編輯器,則將此值設置為 1。|
|連結編輯器|REG_SZ|*\<GUID>*|用於任何可以打開具有代碼頁支援的文件的語言服務。 例如,當您使用**Open With**命令打開 .txt 檔時,將提供用於使用原始碼編輯器的選項,無論是否使用編碼。<br /><br /> 子鍵名稱中指定的 GUID 用於代碼頁編輯器工廠;在此特定註冊表項中指定的連結 GUID 用於常規編輯器工廠。 此條目的目的是,如果 IDE 不使用預設編輯器打開檔,IDE 將嘗試使用清單中的下一個編輯器。 下一個編輯器不應是代碼頁編輯器工廠,因為此編輯器工廠與失敗的編輯器工廠基本相同。|
|Package|REG_SZ|*\<GUID>*|顯示名稱的 ResID 的 VS 包裝 GUID。|

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

## <a name="registry-entries-for-logical-view-options"></a>邏輯檢視選項的註冊表項
 *VS Reg 根*\\\*編輯器 GUI>*_LogicViews 鍵可以包含以下值。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ||未使用的。|
|*\<GUID>*|REG_SZ|""|受支援的邏輯視圖的鍵。 你可以有盡可能多的這些,你需要。 註冊表項的名稱是重要的,而不是值,它始終是一個空字串。|

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

## <a name="registry-entries-for-editor-extension-options"></a>編輯器延伸選項的註冊表項
 *VS Reg 根*\\\*編輯器 GUID*_擴展鍵可以包含以下值。 檔名副檔名不包括前導期間。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|(預設值)|REG_SZ||未使用的。|
|*\<分機>*|REG_DWORD|0-0xffffff|擴展的相對優先順序。 如果兩種或多種語言共用同一擴展名,則選擇優先順序較高的語言。|

 \\此外,目前使用者對編輯器的預設選擇儲存在HKEY_Current_User_軟體\VisualStudio*X.Y*=預設\\編輯器*分機*。所選語言服務的 GUID 位於「自訂」條目中。 這優先適用於當前使用者。

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

## <a name="registry-entries-for-managed-package-framework-language-service-options"></a>託管套件框架語言服務選項的註冊表項
 以下註冊表項特定於託管包框架 (MPF) 語言服務類。 這些註冊表項表示對各種 IntelliSense 功能和其他高級編輯功能的語言服務的支援。

 這些註冊表項通過<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類訪問。

|名稱|類型|範圍|描述|
|----------|----------|-----------|-----------------|
|程式碼感知|REG_DWORD|0-1|支援 IntelliSense 操作。|
|匹配支架|REG_DWORD|0-1|支援匹配的語言對,如大括弧、括弧和括弧。|
|QuickInfo|REG_DWORD|0-1|支援"感知快速資訊"操作。|
|顯示符合支架|REG_DWORD|0-1|支援在狀態列中顯示匹配的語言對。|
|符合支架AtCaret|REG_DWORD|0-1|支援顯示匹配的語言對,通常通過突出顯示這兩個元素。|
|最大錯誤訊息|REG_DWORD|0-n|可在 **「錯誤清單」** 視窗中顯示的最大錯誤數。|
|程式碼感知延遲|REG_DWORD|0-n|啟動 IntelliSense 操作的任何背景分析之前要延遲的毫秒數。|
|開啟同步完成|REG_DWORD|0-1|支援後台分析。|
|開啟註解|REG_DWORD|0-1|支援註釋出選定的文本塊,還意味著支援未註釋的選定文本。|
|開啟格式選擇|REG_DWORD|0-1|支援格式化文本,如自動縮進或調整大括弧的位置。|
|自動離開|REG_DWORD|0-1|支持大綱(可摺疊的區域)。|
|最大區域|REG_DWORD|0-n|每個檔的最大隱藏區域數。|

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
