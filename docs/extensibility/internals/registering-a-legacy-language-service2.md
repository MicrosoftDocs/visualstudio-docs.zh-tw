---
title: 註冊舊版語言 Service2 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, language services
- language services, registry information
- registry, language services
ms.assetid: ca312aa3-f9f1-4572-8553-89bf3a724deb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cb7750f55bd9175c552aa765d21b1334f5f1dfe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="registering-a-legacy-language-service"></a>註冊舊版語言服務
下列各節提供的登錄項目清單的各種語言中可用的服務選項[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 登錄項目下, 面*VS Reg 根*等於 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*X.Y*，其中*X.Y*是[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]版本號碼。  
  
## <a name="registry-entries-for-language-service-options"></a>語言服務選項的登錄項目  
 *VS Reg 根*\Languages\Language 服務\\*語言名稱*索引鍵可包含下列值。  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|(預設值)|REG_SZ|*\<GUID &GT;*|語言服務的 GUID。|  
|LangResID|REG_DWORD|0x0-0xffff|資源識別元 (ResID) 語言的當地語系化的文字名稱的字串。|  
|Package|REG_SZ|*\<GUID &GT;*|VSPackage 的 GUID。|  
|ShowCompletion|REG_DWORD|0-1|指定是否**陳述式完成**中選項**選項**對話方塊的 已啟用。|  
|ShowSmartIndent|REG_DWORD|0-1|指定是否可以選取**智慧**中縮排**選項**對話方塊的 已啟用。|  
|RequestStockColors|REG_DWORD|0-1|指定是否自訂或色彩關鍵字使用的預設色彩。|  
|ShowHotURLs|REG_DWORD|0-1|指定使用者是否可以按一下 Url。|  
|預設為非作用的 Url|REG_DWORD|0-1|指定的初始設定**啟用按一下方式的 URL 導覽**選項**選項** 對話方塊。|  
|DefaultToInsertSpaces|REG_DWORD|0-1|指定語言服務是否有 「 插入空格 」 做為其預設值 索引標籤選項。|  
|ShowDropdownBarOption|REG_DWORD|0-1|啟用或停用**導覽列**選項**選項**對話方塊，顯示或隱藏**導覽列**。|  
|僅適用於單一程式碼視窗|REG_DWORD|0-1|啟用或停用**新視窗**中選擇**視窗**語言服務的功能表。|  
|EnableAdvancedMembersOption|REG_DWORD|0-1|啟用或停用**選項**的對話方塊設定**隱藏進階成員**。|  
|支援 CF_HTML|REG_DWORD|0-1|指定複製及貼上的資料將 HTML 編輯器是否會啟用。|  
|EnableLineNumbersOption|REG_DWORD|0-1|指定是否**行號**中選項**選項**語言服務已啟用 對話方塊。|  
|HideAdvancedMembersByDefault|REG_DWORD|0-1|指定完成清單中是否會隱藏進階的成員，例如私用欄位。|  
|ShowBraceCompletion|REG_DWORD|0-1|指定是否**大括號完成**選項**選項**對話方塊的 已啟用。|  
  
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
  
## <a name="registry-entries-for-debugger-languages-options"></a>偵錯工具的語言選項的登錄項目  
 *VS Reg 根*\Languages\Language 服務\\*語言名稱*\Debugger 語言\\*GUID*\ 金鑰可包含下列值。  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|(預設值)|REG_SZ|文字|預設值可以用於文件的語言名稱。 此索引鍵的名稱是有對應的項目中的運算式評估工具的 GUID  *\<VS 登錄根目錄 >* \AD7Metrics\Expression 評估工具。|  
  
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
 您可以新增登錄機碼 EditorToolsOptions 機碼下的屬性頁和屬性節點。 這些索引鍵和其值會識別在屬性頁**選項**對話方塊 (上**工具**功能表)，可用來設定語言服務。 在下列範例中，*頁面名稱*屬性頁面中，名稱和*節點名稱*位於樹狀結構中節點的名稱**選項** 對話方塊。 必須分別指定頁面項目和節點的項目。  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|(預設值)|REG_SZ|resID|此選項頁面的當地語系化的顯示名稱。 名稱可以是常值文字或 #`nnn`，其中`nnn`附屬 DLL 的指定 VSPackage 中字串資源 id。|  
|Package|REG_SZ|*GUID*|實作這個選項頁面的 VSPackage 的 GUID。|  
|頁面|REG_SZ|*GUID*|藉由呼叫要求從 VSPackage 的屬性頁 GUID<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>方法。 如果這個登錄項目不存在，則登錄機碼描述節點，而不是頁面。|  
  
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
 副檔名的項目應該包含前置的句點，例如".myext"。  
  
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
 *VS Reg 根*\Editors 索引鍵可包含下列值：  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|(預設值)|REG_SZ|""|未使用。您可以將您的名稱的文件。|  
|DefaultToolboxTab|REG_SZ|""|編輯器在作用中時，進行預設 [工具箱] 索引標籤的名稱。|  
|DisplayName|REG_SZ|resID|要顯示在 [名稱**開啟**] 對話方塊。 名稱是標準格式字串資源識別碼或名稱。|  
|ExcludeDefTextEditor|REG_DWORD|0-1|用於**開啟**功能表命令。 如果您不想要列出可用的編輯器，為特定檔案類型清單中的預設文字編輯器，設定此值為 1。|  
|LinkedEditorGUID|REG_SZ|*\<GUID &GT;*|用於可以開啟檔案與字碼頁支援任何語言服務。 例如，當您開啟.txt 檔使用**開啟**命令時，提供使用原始程式碼編輯器，逾時或無編碼的選項。<br /><br /> 指定名稱之子機碼 GUID 為字碼頁編輯器 factory。這個特定的登錄項目中指定的連結的 GUID 是規則編輯器 factory。 此項目的是，如果在 IDE 不會使用預設編輯器開啟檔案，IDE 會嘗試使用清單中的下一個編輯器。 這個下一個編輯器應該不是字碼頁編輯器 factory，因為這個編輯器 factory 基本上是 editor factory 失敗的相同。|  
|Package|REG_SZ|*\<GUID &GT;*|顯示名稱 ResID VSPackage GUID。|  
  
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
  
## <a name="registry-entries-for-logical-view-options"></a>邏輯檢視選項的登錄項目  
 *VS Reg 根*\Editors\\*編輯器 GUI >* \LogicalViews 索引鍵可包含下列值。  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|(預設值)|REG_SZ||未使用。|  
|*\<GUID &GT;*|REG_SZ|""|支援的邏輯檢視的索引鍵。 您可以視需要有最大數量的這些。 登錄項目名稱會是很重要的不是值，都是空字串。|  
  
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
  
## <a name="registry-entries-for-editor-extension-options"></a>編輯器延伸模組選項的登錄項目  
 *VS Reg 根*\Editors\\*編輯器 GUID*\Extensions 索引鍵可包含下列值。 檔案名稱的副檔名不包含前置句號。  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|(預設值)|REG_SZ||未使用。|  
|*\<ext >*|REG_DWORD|0 0xffffffff|擴充功能的相對優先權。 如果兩個或多個語言共用同一個延伸模組，則會選擇較高優先順序的語言。|  
  
 此外，目前使用者的編輯器的預設選取項目會儲存在 HKEY_Current_User\Software\Microsoft\VisualStudio\\*X.Y*\Default 編輯器\\*ext*。選取的語言服務的 GUID 是在自訂項目。 這個選項的目前使用者的優先順序。  
  
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
 下列的登錄項目僅適用於 managed 的封裝架構 (MPF) 語言服務類別。 這些登錄項目指示在不同的 IntelliSense 功能以及其他進階編輯功能之語言服務的支援。  
  
 這些登錄項目透過存取<xref:Microsoft.VisualStudio.Package.LanguagePreferences>類別。  
  
|名稱|類型|範圍|描述|  
|----------|----------|-----------|-----------------|  
|CodeSense|REG_DWORD|0-1|IntelliSense 作業的支援。|  
|MatchBraces|REG_DWORD|0-1|支援的語言組，例如大括號、 括號和方括號比對。|  
|QuickInfo|REG_DWORD|0-1|IntelliSense 快速諮詢作業的支援。|  
|ShowMatchingBrace|REG_DWORD|0-1|在狀態列中顯示相符的語言配對的支援。|  
|MatchBracesAtCaret|REG_DWORD|0-1|支援顯示語言配對，通常是透過反白顯示兩個項目。|  
|MaxErrorMessages|REG_DWORD|0-n|可在顯示的錯誤數目上限**錯誤清單**視窗。|  
|CodeSenseDelay|REG_DWORD|0-n|若要延遲啟動任何背景剖析 IntelliSense 作業之前的毫秒數。|  
|EnableAsyncCompletion|REG_DWORD|0-1|背景剖析支援。|  
|EnableCommenting|REG_DWORD|0-1|支援的標記為註解選取的文字區塊，且也表示取消選取的文字支援。|  
|EnableFormatSelection|REG_DWORD|0-1|格式化文字，例如自動縮排或調整大括號位置的支援。|  
|AutoOutlining|REG_DWORD|0-1|支援的大綱 （可摺疊的區域）。|  
|MaxRegions|REG_DWORD|0-n|每個檔案的隱藏區域的數目上限。|  
  
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
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)