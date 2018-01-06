---
title: "繫結至功能表項目的鍵盤快速鍵 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ceae0f2ea69ce0340565abb85bb002713010407d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>繫結之功能表項目的的鍵盤快速鍵
要繫結的自訂功能表命令鍵盤快速鍵，只要加入.vsct 檔以取得封裝的項目。 本主題說明如何將鍵盤快速鍵對應至自訂按鈕、 功能表項目或工具列命令，以及如何套用的預設編輯器中的鍵盤對應，或將它限制為自訂編輯器。  
  
 若要將鍵盤快速鍵指派給現有的 Visual Studio 功能表項目，請參閱[識別及自訂鍵盤快速鍵](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)。  
  
## <a name="choosing-a-key-combination"></a>選擇的按鍵組合  
 Visual Studio 中已使用許多的鍵盤快速鍵。 您不應該指派至一個以上的命令相同的快顯，因為很難偵測到重複的繫結，而且也可能會造成無法預期的結果。 因此，最好確認捷徑的可用性，才能將它指派。  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>若要確認可用性的鍵盤快速鍵  
  
1.  在**工具 / 選項 / 環境**視窗中，選取**鍵盤**。  
  
2.  請確定**新的快速鍵用於**設**Global**。  
  
3.  在**按快速鍵**方塊中，輸入您想要使用的鍵盤快速鍵。  
  
     如果已經在 Visual Studio 中，使用捷徑**目前所使用的捷徑**方塊會顯示目前呼叫的捷徑命令。  
  
4.  嘗試不同的組合索引鍵，直到找到沒有對應。  
  
    > [!NOTE]
    >  使用 alt 鍵的鍵盤快速鍵可能開啟功能表，並不是直接執行命令。 因此，**目前所使用的捷徑**方塊可能是空白，當您輸入包含 ALT 捷徑。 您可以確認捷徑不會透過關閉開啟的功能表**選項**對話方塊，然後按下按鍵。  
  
 下列程序假設您有現有的 VSPackage 的功能表命令。 如果您需要這麼做可協助，看看[建立擴充的功能表命令](../extensibility/creating-an-extension-with-a-menu-command.md)。  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>若要指派給命令的鍵盤快速鍵  
  
1.  開啟.vsct 檔，為您的封裝。  
  
2.  建立空白`<KeyBindings>`區段之後`<Commands>`如果尚不存在。  
  
    > [!WARNING]
    >  如需索引鍵繫結的詳細資訊，請參閱[Keybinding](../extensibility/keybinding-element.md)。  
  
     在`<KeyBindings>`區段中，建立`<KeyBinding>`項目。  
  
     設定`guid`和`id`屬性，將所要叫用的命令。  
  
     設定`mod1`屬性**控制項**， **Alt**，或**Shift**。  
  
     按鍵組合區段看起來應該像這樣：  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 如果您的鍵盤快速鍵需要兩個以上的索引鍵，請設定`mod2`和`key2`屬性。  
  
 在大部分情況下， **Shift**不應使用沒有第二個修飾詞因為已按下它會導致大部分英數字元的按鍵輸入大寫的字母或符號。  
  
 虛擬按鍵碼可讓您存取而沒有字元，例如函式的索引鍵與其相關聯的特殊按鍵和**退格鍵**索引鍵。 如需詳細資訊，請參閱[虛擬按鍵碼](http://go.microsoft.com/fwlink/?LinkID=105932)。  
  
 若要使用此命令在 Visual Studio 編輯器，請設定`editor`屬性`guidVSStd97`。  
  
 若要使此命令只適用於自訂編輯器，設定`editor`屬性名稱的自訂編輯器所產生[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]封裝範本，當您建立 VSPackage，包括自訂編輯器。 若要尋找的名稱值，請查看`<Symbols>`區段`<GuidSymbol>`節點其`name`屬性以"`editorfactory`。 」這是自訂編輯器的名稱。  
  
## <a name="example"></a>範例  
 此範例中繫結至名為命令的鍵盤快速鍵 CTRL + ALT + C`cmdidMyCommand`名為封裝中`MyPackage`。  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>範例  
 此範例中繫結至名為命令的鍵盤快速鍵 CTL + B`cmdidBold`在專案中名為`TestEditor`。 此命令為可用，只能在自訂編輯器中，而不是在其他編輯器。  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>請參閱  
 [擴充功能表和命令](../extensibility/extending-menus-and-commands.md)