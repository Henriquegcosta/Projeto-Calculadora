<h1 align="center">Projeto Calculadora 📱</h1>

### Sobre o Projeto

- Esse projeto foi desenvolvido com o intuito de praticar a criação de UI com XML. Foi bem interessante criar esse projeto, aprendi a utilização de Linear Layouts.
> Além da utilização de conceitos que nunca havia utilizado. Por exemplo o método contains
- Foi desenvolvido junto do curso de Desenvolvimento Android Kotlin na Udemy.
- Atualmente ela so funciona com contas simples e rápidas.


<br>


<p align="center">
  <img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/ImageCalc1.jpeg" width="250" title="hover text">
  <img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/ImageCalc2.jpeg" width="250" title="hover text">
  <img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/ImageCalc3.jpeg" width="250" title="hover text">
</p>


<br>


## Em funcionamento:

<p align="center">
<img src="https://github.com/Henriquegcosta/Henriquegcosta/blob/main/images/CalculadoraGif.gif" width="450" title="hover text">
</p>

## Codigo do projeto. **(KOTLIN)**

``` 
    private var tvInput : TextView? = null
    var lastNumeric : Boolean = false
    var lastDot : Boolean = false

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        tvInput = findViewById(R.id.tvInput)

    }


    // Funçao para digitar os numeros
    fun onDigit(view: View){


        // Faz a view como botão facilitando a identificação de qual botão você clickou, evitando repetição de codigo
        tvInput?.append((view as Button).text)


        lastNumeric = true
        lastDot = false
    }

    // Funçao para limpar a tela
    fun onClear(view: View){
        tvInput?.text = " "
    }

    // Função para adicionar numeros decimais
    fun onDecimalPoint(view: View){
        if(lastNumeric && !lastDot){
            tvInput?.append(".")
            lastNumeric = false
            lastDot = true
        }
    }

    fun onOperator(view: View){
        tvInput?.text?.let{
            if(lastNumeric && !isOperatorAdded(it.toString())){
                tvInput?.append((view as Button).text)
                lastNumeric = false
                lastDot = false
            }

        }
    }

    fun onEqual(view: View){
        if(lastNumeric){
            var tvValue = tvInput?.text.toString()
            var prefix = ""

            try{
                if(tvValue.startsWith("-")){
                    prefix = "-"
                    tvValue = tvValue.substring(1)
                }

                if(tvValue.contains("-")){
                    val splitValue = tvValue.split("-")
                    var one = splitValue[0]
                    var two = splitValue[1]

                    if(prefix.isNotEmpty()){
                        one = prefix + one
                    }

                    tvInput?.text = removeZeroAfDot((one.toDouble() - two.toDouble()).toString())
                } else if(tvValue.contains("+")){
                    val splitValue = tvValue.split("+")
                    var one = splitValue[0]
                    var two = splitValue[1]

                    if(prefix.isNotEmpty()){
                        one = prefix + one
                    }

                    tvInput?.text = removeZeroAfDot((one.toDouble() + two.toDouble()).toString())
                } else if(tvValue.contains("/")){
                    val splitValue = tvValue.split("/")
                    var one = splitValue[0]
                    var two = splitValue[1]

                    if(prefix.isNotEmpty()){
                        one = prefix + one
                    }

                    tvInput?.text = removeZeroAfDot((one.toDouble() / two.toDouble()).toString())
                } else if(tvValue.contains("*")){
                    val splitValue = tvValue.split("*")
                    var one = splitValue[0]
                    var two = splitValue[1]

                    if(prefix.isNotEmpty()){
                        one = prefix + one
                    }

                    tvInput?.text = removeZeroAfDot((one.toDouble() * two.toDouble()).toString())
                }


            }catch (e: ArithmeticException){
                e.printStackTrace()
            }
        }
    }

    private fun removeZeroAfDot(result: String) : String{
        var value = result
        if(result.contains(".0"))
            value = result.substring(0, result.length - 2)

        return value
    }

    // Ele nos dira se no texto há um sinal de / * + -, a menos que esteja no inicio
    private fun isOperatorAdded(value: String) : Boolean{
        return if(value.startsWith("-")){
            false
        }else{
            value.contains("/")
                    || value.contains("*")
                    || value.contains("+")
                    || value.contains("-")
        }
    }
```


## Sobre mim

Meu nome é Henrique, tenho 18 anos e estou começando no Desenvolvimento Android. Sempre tive um amor especial por Desenvolvimento Android e agora estou focando em me desenvolver nessa área
Atualmente estou programando apenas em Kotlin. Pretendo aprender Flutter ou Swift futuramente.

Para saber mais sobre minha rotina de uma olhada em meu [Linkedin](https://www.linkedin.com/in/henriquegcosta/) e podemos conversar um pouco mais!.
