---
title: 如何：建立。.Vsct 檔案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating
ms.assetid: b955f51c-f9f9-49c3-a8e4-63b6eb0e0341
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a2483c000bb7c9446ac51bb94ef4006a7b2ac89f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158348"
---
# <a name="how-to-create-a-vsct-file"></a>如何：建立 .Vsct 檔案
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

有幾種方式可以建立以 XML 為基礎的 Visual Studio 命令資料表設定 (. .vsct) 檔。  
  
- 您可以在套件範本中建立新的 VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
- 您可以使用以 XML 為基礎的命令資料表設定編譯器 Vsct.exe，從現有的 .ctc 檔產生檔案。  
  
- 您可以使用 Vsct.exe 從現有的 cto 檔產生 .vsct 檔案。  
  
- 您可以手動建立新的 .vsct 檔案。  
  
  本主題說明如何以手動方式建立新的 .vsct 檔案。  
  
### <a name="to-manually-create-a-new-vsct-file"></a>手動建立新的 .vsct 檔案  
  
1. 啟動 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
2. 在 [ **檔案** ] 功能表上，指向 [ **新增**]，然後按一下 [ **檔案**]。  
  
3. 在 [ **範本** ] 窗格中，按一下 [ **XML** 檔案]，然後按一下 [ **開啟**]。  
  
4. 在 [ **View** ] 功能表上，按一下 [ **屬性視窗]** 以顯示 XML 檔案的屬性。  
  
5. 在 [ **屬性** ] 視窗中，按一下 [架構] 屬性上的 [流覽 ( ... ) ] 按鈕。  
  
6. 在 XSD 架構清單中，選取 .vsct .xsd 架構。 如果它不在清單中，請按一下 [ **新增** ]，然後在本機磁片磁碟機上尋找檔案。 當您完成時，請按一下 **[確定]** 。  
  
7. 在 XML 檔案中，輸入 `<CommandTable` ，然後按 tab 鍵。 輸入以關閉標記 `>` 。  
  
     這會建立基本的 .vsct 檔案。  
  
8. 根據 [.Vsct 架構](../../extensibility/vsct-xml-schema-reference.md)，填入您想要新增的 XML 檔案元素。 如需詳細資訊，請參閱[撰寫。.Vsct](../../extensibility/internals/authoring-dot-vsct-files.md)檔案  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 只要將 .vsct 檔案新增至專案，就不會使其進行編譯。 您必須將它併入組建流程中。  
  
### <a name="to-add-a-vsct-file-to-project-compilation"></a>將 .vsct 檔案新增至專案編譯  
  
1. 在編輯器中開啟您的專案檔。 如果載入專案，您必須先將它卸載。  
  
2. 加入包含 VSCTCompile 元素的 [ItemGroup](../../msbuild/itemgroup-element-msbuild.md) 專案，如下列範例所示。  
  
    ```xml  
    <ItemGroup>  
      <VSCTCompile Include="TopLevelMenu.vsct">  
        <ResourceName>Menus.ctmenu</ResourceName>  
      </VSCTCompile>  
    </ItemGroup>  
  
    ```  
  
     CoNtext.resourcename 元素應一律設為 `Menus.ctmenu` 。  
  
3. 如果您的專案包含 .resx 檔，請加入包含 MergeWithCTO 專案的 EmbeddedResource 元素，如下列範例所示。  
  
    ```xml  
    <EmbeddedResource Include="VSPackage.resx">  
      <MergeWithCTO>true</MergeWithCTO>  
      <ManifestResourceName>VSPackage</ManifestResourceName>  
    </EmbeddedResource>  
  
    ```  
  
     這項標記應該會在包含內嵌資源的 ItemGroup 元素內。  
  
4. 在編輯器中，開啟通常名為 *專案名稱*Package.cs 或 *專案名稱*的封裝檔案。  
  
5. 將 ProvideMenuResource 屬性新增至 package 類別，如下列範例所示。  
  
    ```csharp  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    ```  
  
     第一個參數值必須符合您在專案檔中定義的 [CoNtext.resourcename] 屬性值。  
  
## <a name="see-also"></a>另請參閱  
 [創作。.Vsct 檔案](../../extensibility/internals/authoring-dot-vsct-files.md)   
 [Visual Studio 命令表格 (。.Vsct) 檔案](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [如何：建立。從現有的 .vsct 檔案。.Ctc 檔案](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-ctc-file.md)   
 [如何：建立。從現有的 .vsct 檔案。Cto 檔案](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md)   
 [VSCT XML 結構描述參考](../../extensibility/vsct-xml-schema-reference.md)
