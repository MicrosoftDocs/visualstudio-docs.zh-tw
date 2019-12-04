---
title: 使用 ClickOnce 部署 COM 元件 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6c83367881b7ed6a69fe10af8b7c68eb1692e3e6
ms.sourcegitcommit: 49ebf69986713e440fd138fb949f1c0f47223f23
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74706886"
---
# <a name="deploying-com-components-with-clickonce"></a>使用 ClickOnce 部署 COM 元件
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

傳統 COM 元件的部署通常是一項艱難的任務。 元件需要全域註冊，因此可能會在重迭的應用程式之間造成不適當的副作用。 這種情況通常不是 .NET Framework 應用程式的問題，因為元件完全獨立于應用程式或與並存相容。 Visual Studio 可讓您在 Windows XP 或更高版本的作業系統上部署隔離的 COM 元件。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 提供一個簡單又安全的機制來部署您的 .NET 應用程式。 不過，如果您的應用程式使用舊版 COM 元件，您將需要採取額外的步驟來部署它們。 本主題描述如何部署隔離的 COM 元件和參考原生元件（例如，從 Visual Basic 6.0 或 Visual C++）。  
  
 如需部署隔離的 COM 元件的詳細資訊，請參閱[使用 ClickOnce 和免註冊的 Com 簡化應用程式部署](/archive/msdn-magazine/2005/april/simplify-app-deployment-with-clickonce-and-registration-free-com)。  
  
## <a name="registration-free-com"></a>免註冊的 COM  
 免註冊的 COM 是部署和啟用隔離 COM 元件的新技術。 其運作方式是將所有元件的型別程式庫和註冊資訊（通常安裝在系統登錄中）放入稱為資訊清單的 XML 檔案，並儲存在與應用程式相同的資料夾中。  
  
 隔離 COM 元件需要在開發人員的電腦上註冊，但不需要在終端使用者的電腦上註冊。 若要隔離 COM 元件，您只需要將其參考的**隔離**屬性設定為**True**。 根據預設，這個屬性會設定為**False**，表示應該將它視為已註冊的 COM 參考。 如果此屬性為**True**，則會在組建階段產生此元件的資訊清單。 它也會在安裝期間，將對應的檔案複製到應用程式資料夾。  
  
 當資訊清單產生器遇到隔離的 COM 參考時，它會列舉元件類型程式庫中的所有 `CoClass` 專案，將每個專案與其對應的註冊資料進行比對，並為類型程式庫檔案中的所有 COM 類別產生資訊清單定義。  
  
## <a name="deploying-registration-free-com-components-using-clickonce"></a>使用 ClickOnce 部署免註冊的 COM 元件  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署技術非常適合用來部署隔離的 COM 元件，因為 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 和免註冊的 COM 都要求元件必須有資訊清單才能部署。  
  
 一般而言，元件的作者應該提供資訊清單。 不過，如果沒有，則 Visual Studio 能夠自動產生 COM 元件的資訊清單。 資訊清單產生會在 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 發佈程式期間執行;如需詳細資訊，請參閱[發行 ClickOnce 應用程式](../deployment/publishing-clickonce-applications.md)。 這項功能也可讓您利用在舊版開發環境（例如 Visual Basic 6.0）中所撰寫的舊版元件。  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 部署 COM 元件的方法有兩種：  
  
- 使用啟動載入器來部署您的 COM 元件;這適用于所有支援的平臺。  
  
- 使用原生元件隔離（也稱為免註冊 COM）部署。 不過，這只適用于 Windows XP 或更高版本的作業系統。  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>隔離和部署簡單 COM 元件的範例  
 為了示範免註冊的 COM 元件部署，此範例會在 Visual Basic 中建立以 Windows 為基礎的應用程式，以參考使用 Visual Basic 6.0 建立的隔離原生 COM 元件，並使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]加以部署。  
  
 首先，您將需要建立原生 COM 元件：  
  
##### <a name="to-create-a-native-com-component"></a>若要建立原生 COM 元件  
  
1. 使用 Visual Basic 6.0，**從 [檔案**] 功能表中，依序按一下 [**新增**]、[**專案**]。  
  
2. 在 [**新增專案**] 對話方塊中，選取 [ **Visual Basic** ] 節點，然後選取 [ **ActiveX DLL**專案]。 在 [名稱] 方塊中，輸入 `VB6Hello`。  
  
    > [!NOTE]
    > 只有免註冊的 COM 才支援 ActiveX DLL 和 ActiveX 控制項專案類型;不支援 ActiveX EXE 和 ActiveX 檔專案類型。  
  
3. 在**方案總管**中，按兩下 [ **Class1** ] 以開啟 [文字編輯器]。  
  
4. 在 Class1 中，將下列程式碼新增至 `New` 方法的產生程式碼之後：  
  
    ```  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5. 建立元件。 從 [**建立**] 功能表中，按一下 [**建立方案**]。  
  
> [!NOTE]
> 免註冊的 COM 僅支援 Dll 和 COM 控制項專案類型。 您不能搭配免註冊 COM 使用 Exe。  
  
 現在您可以建立以 Windows 為基礎的應用程式，並在其中新增 COM 元件的參考。  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>若要使用 COM 元件建立以 Windows 為基礎的應用程式  
  
1. 使用 Visual Basic，**從 [檔案**] 功能表中，依序按一下 [**新增**]、[**專案**]。  
  
2. 在 [**新增專案**] 對話方塊中，選取 [ **Visual Basic** ] 節點，然後選取 [ **Windows 應用程式**]。 在 [名稱] 方塊中，輸入 `RegFreeComDemo`。  
  
3. 在**方案總管**中，按一下 [**顯示所有**檔案] 按鈕以顯示專案參考。  
  
4. 以滑鼠右鍵按一下 [**參考**] 節點，然後從內容功能表中選取 [**新增參考**]。  
  
5. 在 [**加入參考**] 對話方塊中，按一下 [**流覽**] 索引標籤，流覽至 [VB6Hello]，然後選取它。  
  
    **VB6Hello**參考會出現在 [參考] 清單中。  
  
6. 指向 [**工具箱**]，選取 [ **Button** ] 控制項，然後將它拖曳至 [ **Form1** ] 表單。  
  
7. 在 [**屬性**] 視窗中，將按鈕的**Text**屬性設定為**Hello**。  
  
8. 按兩下按鈕以加入處理常式程式碼，然後在程式碼檔案中加入程式碼，讓處理常式讀取如下：  
  
   ```  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. 執行應用程式。 從 [**調試**] 功能表中，按一下 [**開始調試**]。  
  
   接下來，您需要隔離控制項。 您的應用程式所使用的每個 COM 元件會在您的專案中表示為 COM 參考。 這些參考會顯示在 [**方案總管**] 視窗的 [**參考**] 節點底下。 （請注意，您可以直接使用 [**專案**] 功能表上的 [**加入參考**] 命令，或將 ActiveX 控制項拖曳至表單上，間接加入參考）。  
  
   下列步驟顯示如何隔離 COM 元件，併發行包含隔離控制項的已更新應用程式：  
  
##### <a name="to-isolate-a-com-component"></a>若要隔離 COM 元件  
  
1. 在**方案總管**的 [**參考**] 節點中，選取 [ **VB6Hello** ] 參考。  
  
2. 在 [**屬性**] 視窗中，將 [**獨立**] 屬性的值從 [ **False** ] 變更為 [ **True**]。  
  
3. 從 [**建立**] 功能表中，按一下 [**建立方案**]。  
  
   現在，當您按下 F5 時，應用程式會如預期般運作，但它現在是在免註冊的 COM 下執行。 為了證明這一點，請嘗試取消註冊 VB6Hello 元件，並在 Visual Studio IDE 外部執行 RegFreeComDemo1。 這次按一下按鈕時，它仍然可以運作。 如果您暫時重新命名應用程式資訊清單，則會再次失敗。  
  
> [!NOTE]
> 您可以藉由暫時將 COM 元件取消註冊來模擬其是否存在。 開啟命令提示字元，輸入 `cd /d %windir%\system32`，移至您的 [系統] 資料夾，然後輸入 `regsvr32 /u VB6Hello.dll`取消註冊元件。 您可以輸入 `regsvr32 VB6Hello.dll`來重新註冊它。  
  
 最後一個步驟是使用 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]發行應用程式：  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>若要使用隔離的 COM 元件發行應用程式更新  
  
1. 從 [**建立**] 功能表中，按一下 [**發佈 RegFreeComDemo**]。  
  
    會顯示 [組態精靈]。  
  
2. 在 [發行嚮導] 中，指定本機電腦磁片上的位置，您可以在其中存取及檢查已發行的檔案。  
  
3. 按一下 [完成] 發佈應用程式。  
  
   如果您檢查已發佈的檔案，您將會注意到已包含系統監視器檔案。 控制項完全獨立于此應用程式，也就是說，如果使用者的電腦有另一個應用程式使用不同版本的控制項，就無法干擾此應用程式。  
  
## <a name="referencing-native-assemblies"></a>參考原生元件  
 Visual Studio 支援對原生 Visual Basic 6.0 或C++元件的參考;這類參考稱為原生參考。 您可以藉由驗證其 [**檔案類型**] 屬性設為 [**原生**] 或 [ **ActiveX**]，來判斷參考是否為原生。  
  
 若要加入原生參考，請使用 [**加入參考**] 命令，然後流覽至資訊清單。 有些元件會將資訊清單放在 DLL 內。 在此情況下，您可以直接選擇 DLL 本身，如果偵測到元件包含內嵌的資訊清單，Visual Studio 會將它新增為原生參考。 Visual Studio 也會自動包含資訊清單中所列出的任何相依檔案或元件（如果它們位於與所參考元件相同的資料夾中）。  
  
 COM 控制項隔離可讓您輕鬆地部署尚未擁有資訊清單的 COM 元件。 不過，如果元件是以資訊清單提供，您可以直接參考資訊清單。 事實上，您應該盡可能使用元件作者所提供的資訊清單，而不是使用**獨立**的屬性。  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>免註冊 COM 元件部署的限制  
 免註冊的 COM 透過傳統部署技術提供了明顯的優勢。 不過，有幾個限制和警告也應該指出。最大的限制是它只適用于 Windows XP 或更新版本。 免註冊 COM 的執行需要變更元件在核心作業系統中的載入方式。 可惜的是，沒有免註冊 COM 的下層支援層級。  
  
 並非每個元件都是免註冊 COM 的合適候選。 如果下列其中一項為真，則元件不適用：  
  
- 元件是跨進程伺服器。 不支援 EXE 伺服器;僅支援 Dll。  
  
- 元件是作業系統的一部分，或是系統元件（例如 XML、Internet Explorer 或 Microsoft Data Access Components （MDAC））。 您應遵循元件作者的轉散發原則;請洽詢您的廠商。  
  
- 元件是應用程式的一部分，例如 Microsoft Office。 例如，您不應該嘗試隔離 Microsoft Excel 物件模型。 這是 Office 的一部分，只能用於已安裝完整 Office 產品的電腦。  
  
- 此元件是用來做為增益集或嵌入式管理單元，例如，Office 增益集或網頁瀏覽器中的控制項。 這類元件通常需要由裝載環境定義的某種註冊配置，超出資訊清單本身的範圍。  
  
- 此元件會管理系統的實體或虛擬裝置，例如列印多工緩衝處理器的設備磁碟機。  
  
- 此元件是資料存取可轉散發套件。 資料應用程式通常需要先安裝個別的資料存取可轉散發套件，才能執行。 您不應該嘗試隔離元件，例如 Microsoft ADO 資料控制、Microsoft OLE DB 或 Microsoft Data Access Components （MDAC）。 相反地，如果您的應用程式使用 MDAC 或 SQL Server Express，您應該將它們設為必要條件。請參閱[如何： 使用 ClickOnce 應用程式的安裝必要條件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)。  
  
  在某些情況下，元件的開發人員可能會針對免註冊的 COM 重新設計。 如果無法這麼做，您仍然可以透過使用啟動載入器的標準註冊配置，來建立和發行相依于這些應用程式。 如需詳細資訊，請參閱建立啟動載入器[套件](../deployment/creating-bootstrapper-packages.md)。  
  
  每個應用程式只能隔離一個 COM 元件一次。 例如，您無法將相同的 COM 元件與屬於相同應用程式的兩個不同**類別庫**專案隔離。 這麼做會導致組建警告，而且應用程式將無法在執行時間載入。 為了避免這個問題，Microsoft 建議您將 COM 元件封裝在單一類別庫中。  
  
  在許多情況下，即使應用程式的部署不需要註冊，還是需要在開發人員的電腦上進行 COM 註冊。 `Isolated` 屬性需要在開發人員的電腦上註冊 COM 元件，才能在組建期間自動產生資訊清單。 在組建期間，不會叫用自我註冊的註冊捕捉功能。 此外，未在類型程式庫中明確定義的任何類別都不會反映在資訊清單中。 使用具有預先存在之資訊清單的 COM 元件（例如原生參考）時，元件可能不需要在開發期間註冊。 不過，如果元件為 ActiveX 控制項，而且您想要將它包含在 [工具箱] 和 [Windows Forms 設計**工具**] 中，則需要註冊。  
  
## <a name="see-also"></a>請參閱  
 [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
