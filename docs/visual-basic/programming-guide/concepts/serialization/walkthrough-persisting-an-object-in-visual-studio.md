---
title: persistir um objeto no Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 0b2fff171164a29e6066839371fc95ad41b452f1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086459"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="d875c-102">Passo a passo: mantendo um objeto no Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d875c-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="d875c-103">Embora você possa definir as propriedades de um objeto para os valores padrão em tempo de design, qualquer valor inserido em tempo de execução será perdido quando o objeto for destruído.</span><span class="sxs-lookup"><span data-stu-id="d875c-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="d875c-104">Você pode usar a serialização para manter os dados de um objeto entre instâncias, o que permite armazenar valores e recuperá-los na próxima vez que o objeto for instanciado.</span><span class="sxs-lookup"><span data-stu-id="d875c-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d875c-105">No Visual Basic, para armazenar dados simples, como um nome ou número, você pode usar o objeto `My.Settings`.</span><span class="sxs-lookup"><span data-stu-id="d875c-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="d875c-106">Para obter mais informações, consulte [Objeto My.Settings](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="d875c-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="d875c-107">Neste passo a passo, você criará um objeto `Loan` simples e manterá seus dados em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d875c-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="d875c-108">Em seguida, você recuperará os dados do arquivo quando recriar o objeto.</span><span class="sxs-lookup"><span data-stu-id="d875c-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d875c-109">Este exemplo cria um novo arquivo, se o arquivo ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="d875c-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="d875c-110">Se um aplicativo precisar criar um arquivo, esse aplicativo precisará da permissão `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="d875c-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="d875c-111">Permissões são definidas usando listas de controle de acesso.</span><span class="sxs-lookup"><span data-stu-id="d875c-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="d875c-112">Se o arquivo já existir, o aplicativo precisará somente da permissão `Write`, que é uma permissão menor.</span><span class="sxs-lookup"><span data-stu-id="d875c-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="d875c-113">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder permissões `Read` a um único arquivo (em vez de permissões Create para uma pasta).</span><span class="sxs-lookup"><span data-stu-id="d875c-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="d875c-114">Além disso, é mais seguro gravar dados em pastas de usuário do que na pasta raiz ou na pasta Arquivos de Programas.</span><span class="sxs-lookup"><span data-stu-id="d875c-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d875c-115">Este exemplo armazena dados em um arquivo binário.</span><span class="sxs-lookup"><span data-stu-id="d875c-115">This example stores data in a binary.</span></span> <span data-ttu-id="d875c-116">Esses formatos não devem ser usados para dados confidenciais, como senhas ou informações de cartão de crédito.</span><span class="sxs-lookup"><span data-stu-id="d875c-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d875c-117">As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição.</span><span class="sxs-lookup"><span data-stu-id="d875c-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d875c-118">Para alterar as configurações, clique em **Importar e exportar configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="d875c-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d875c-119">Para obter mais informações, consulte [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d875c-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="d875c-120">Criando o objeto Loan</span><span class="sxs-lookup"><span data-stu-id="d875c-120">Creating the Loan Object</span></span>  

 <span data-ttu-id="d875c-121">A primeira etapa é criar uma classe `Loan` e um aplicativo de teste que usa a classe.</span><span class="sxs-lookup"><span data-stu-id="d875c-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="d875c-122">Para criar a classe Loan</span><span class="sxs-lookup"><span data-stu-id="d875c-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="d875c-123">Crie um novo projeto de Biblioteca de classes e denomine-o “LoanClass".</span><span class="sxs-lookup"><span data-stu-id="d875c-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="d875c-124">Para obter mais informações, consulte [Criando soluções e projetos](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="d875c-124">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="d875c-125">No **Gerenciador de Soluções**, abra o menu de atalho para o arquivo Class1 e escolha **Renomear**.</span><span class="sxs-lookup"><span data-stu-id="d875c-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="d875c-126">Renomeie o arquivo como `Loan` e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="d875c-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="d875c-127">Renomear o arquivo também renomeará a classe para `Loan`.</span><span class="sxs-lookup"><span data-stu-id="d875c-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="d875c-128">Adicione os seguintes membros públicos à classe:</span><span class="sxs-lookup"><span data-stu-id="d875c-128">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="d875c-129">Você também precisará criar um aplicativo simples que usa a classe `Loan`.</span><span class="sxs-lookup"><span data-stu-id="d875c-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="d875c-130">Para criar um aplicativo de teste</span><span class="sxs-lookup"><span data-stu-id="d875c-130">To create a test application</span></span>  
  
1. <span data-ttu-id="d875c-131">Para adicionar um projeto de Aplicativo do Windows Forms à sua solução, no menu **Arquivo**, escolha **Adicionar**, **Novo Projeto**.</span><span class="sxs-lookup"><span data-stu-id="d875c-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="d875c-132">Na caixa de diálogo **Adicionar Novo Projeto**, escolha **Aplicativo do Windows Forms** e insira `LoanApp` como o nome do projeto e clique **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d875c-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="d875c-133">No **Gerenciador de Soluções**, escolha o projeto LoanApp.</span><span class="sxs-lookup"><span data-stu-id="d875c-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="d875c-134">No menu **Projeto**, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="d875c-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="d875c-135">No menu **Projeto**, escolha **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="d875c-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="d875c-136">Na caixa de diálogo **Adicionar Referência**, escolha a guia **Projetos** e escolha o projeto LoanClass.</span><span class="sxs-lookup"><span data-stu-id="d875c-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="d875c-137">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d875c-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="d875c-138">No designer, adicione quatro controles <xref:System.Windows.Forms.TextBox> ao formulário.</span><span class="sxs-lookup"><span data-stu-id="d875c-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="d875c-139">No Editor de Códigos, adicione o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d875c-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="d875c-140">Adicione um manipulador de eventos para o evento `PropertyChanged` do formulário usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d875c-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="d875c-141">Neste ponto, você pode compilar e executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d875c-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="d875c-142">Observe que os valores padrão da classe `Loan` aparecem nas caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="d875c-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="d875c-143">Tente alterar o valor de taxa de juros de 7,5 para 7,1 e, em seguida, feche o aplicativo e execute-o novamente – o valor será revertido para o padrão de 7,5.</span><span class="sxs-lookup"><span data-stu-id="d875c-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="d875c-144">No mundo real, as taxas de juros mudam periodicamente, mas não necessariamente toda vez que o aplicativo for executado.</span><span class="sxs-lookup"><span data-stu-id="d875c-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="d875c-145">Em vez de fazer o usuário atualizar a taxa de juros sempre que o aplicativo for executado, é melhor preservar a taxa de juros mais recente entre instâncias do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d875c-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="d875c-146">Na próxima etapa, você fará exatamente isso adicionando a serialização à classe Loan.</span><span class="sxs-lookup"><span data-stu-id="d875c-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="d875c-147">Usando a serialização para manter o objeto</span><span class="sxs-lookup"><span data-stu-id="d875c-147">Using Serialization to Persist the Object</span></span>  

 <span data-ttu-id="d875c-148">Para manter os valores da classe Loan, primeiro você deve marcar a classe com o atributo `Serializable`.</span><span class="sxs-lookup"><span data-stu-id="d875c-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="d875c-149">Para marcar uma classe como serializável</span><span class="sxs-lookup"><span data-stu-id="d875c-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="d875c-150">Altere a declaração da classe para a classe Loan da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d875c-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="d875c-151">O atributo `Serializable` informa ao compilador que tudo na classe pode ser mantido em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d875c-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="d875c-152">Como o evento `PropertyChanged` é manipulado por um objeto do Windows Forms, ele não pode ser serializado.</span><span class="sxs-lookup"><span data-stu-id="d875c-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="d875c-153">O atributo `NonSerialized` pode ser usado para marcar os membros da classe que não devem ser mantidos.</span><span class="sxs-lookup"><span data-stu-id="d875c-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="d875c-154">Para impedir que um membro seja serializado</span><span class="sxs-lookup"><span data-stu-id="d875c-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="d875c-155">Altere a declaração para o evento `PropertyChanged` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d875c-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="d875c-156">A etapa seguinte é adicionar o código de serialização ao aplicativo LoanApp.</span><span class="sxs-lookup"><span data-stu-id="d875c-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="d875c-157">Para serializar a classe e gravá-la em um arquivo, use os namespaces <xref:System.IO> e <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="d875c-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="d875c-158">Para evitar digitar os nomes totalmente qualificados, você pode adicionar referências às bibliotecas de classe necessárias.</span><span class="sxs-lookup"><span data-stu-id="d875c-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="d875c-159">Para adicionar referências a namespaces</span><span class="sxs-lookup"><span data-stu-id="d875c-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="d875c-160">Adicione as seguintes instruções ao topo da classe `Form1`:</span><span class="sxs-lookup"><span data-stu-id="d875c-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="d875c-161">Nesse caso, você está usando um formatador binário para salvar o objeto em um formato binário.</span><span class="sxs-lookup"><span data-stu-id="d875c-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="d875c-162">A próxima etapa é adicionar código para desserializar o objeto do arquivo quando o objeto for criado.</span><span class="sxs-lookup"><span data-stu-id="d875c-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="d875c-163">Para desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="d875c-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="d875c-164">Adicione uma constante à classe para o nome do arquivo de dados serializado.</span><span class="sxs-lookup"><span data-stu-id="d875c-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="d875c-165">Modifique o código no procedimento do evento `Form1_Load` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="d875c-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="d875c-166">Observe que primeiro você deve verificar se o arquivo existe.</span><span class="sxs-lookup"><span data-stu-id="d875c-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="d875c-167">Se ele existir, crie uma classe <xref:System.IO.Stream> para ler o arquivo binário e uma classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> para converter o arquivo.</span><span class="sxs-lookup"><span data-stu-id="d875c-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="d875c-168">Você também precisa converter do tipo de fluxo para o tipo de objeto Loan.</span><span class="sxs-lookup"><span data-stu-id="d875c-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="d875c-169">Em seguida, você deve adicionar código para salvar os dados inseridos nas caixas de texto na classe `Loan` e, então, precisa serializar a classe em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d875c-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="d875c-170">Para salvar os dados e serializar a classe</span><span class="sxs-lookup"><span data-stu-id="d875c-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="d875c-171">Adicione o seguinte código ao procedimento do evento `Form1_FormClosing`:</span><span class="sxs-lookup"><span data-stu-id="d875c-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="d875c-172">Neste ponto, você pode compilar e executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="d875c-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="d875c-173">Inicialmente, os valores padrão aparecem nas caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="d875c-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="d875c-174">Tente alterar os valores e digite um nome na quarta caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="d875c-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="d875c-175">Feche o aplicativo e execute-o novamente.</span><span class="sxs-lookup"><span data-stu-id="d875c-175">Close the application and then run it again.</span></span> <span data-ttu-id="d875c-176">Observe que agora os novos valores aparecem nas caixas de texto.</span><span class="sxs-lookup"><span data-stu-id="d875c-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d875c-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="d875c-177">See also</span></span>

- [<span data-ttu-id="d875c-178">Serialização (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d875c-178">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="d875c-179">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d875c-179">Visual Basic Programming Guide</span></span>](../../index.md)
