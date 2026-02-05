# Lógica de Programação - IMC e Sistema de Construção / Programação Kotlin

# 1 - 
### Construa um programa que calcule o IMC – Índice de Massa Corporal e ainda exiba a classificação de acordo com a tabela de classificação da OMS. Classificação do IMC:
- Menor que 18,5 - Abaixo do peso
- Entre 18,5 e 24,9 - Peso normal
- Entre 25 e 29,9 - Sobrepeso (acima do peso desejado)
- Igual ou acima de 30 – Obesidade
```
fun main(){
 
    print("Coloque o seu peso: ")
    val peso = readln().toFloat()
    print("Coloque a sua altura: ")
    val altura = readln().toFloat()
  
  	val resultado = IMC(peso, altura)
    
    val status = when{
    resultado < 18.5f -> "Abaixo do peso"
    resultado >= 18.5f && resultado <= 24.9f -> "Peso normal"
    resultado >= 25f && resultado <= 29.9f -> "Sobrepeso"
	resultado >= 30f -> "Obesidade"
    else -> "Valor invalido"
    }
 
 	println(status)
}

fun IMC (peso: Float, altura: Float): Float{
    return peso / (altura * altura)
    
}
```

# 2 -
### A construtora Prudente S.A atua no segmento de construção civil, e recentemente fechou contrato para construção de casas para um novo lançamento que terá diversas plantas diferentes. Para auxiliar no cálculo de despesas e mão de obra, construa um programa que:
a. Calcule a área do terreno
b. Calcule quantos profissionais serão necessários na obra a partir da tabela. A construtora só realiza contrato a partir de 10M2.
 - 1 Metre de obra / A partir de 10 M² /
 - 2 Serventes    / A cada 10 m² /
 - 1 Engenheiro   / A cada 100 m² /

c. Calcule ainda o valor da obra a partir da tabela abaixo:
  - A cada 10 m² / R$ 4.500,00
  - 1 quartos sem suíte / Acrescentar R$ 12.000,00
  - 1 área de serviço / Acrescentar R$ 15.000,00
  - 1 piscina / Acrescentar R$ 27.550,00
  - 1 quarto com suíte / Acrescentar R$ 17.000,00
  - 1 banheiro / Acrescentar R$ 5.000,00

d. Calcule o valor a ser pago com mão de obra de acordo com a tabela
  - 1 Metre de obra / R$ 3.500,00
  - 1 Serventes / R$ 1.900,00
  - 1 Engenheiro / R$ 11.000,00

e. Calcule o valor total da obra e exiba o relatório.
  1. Subtotal por item (Conforme tabela)
  2. Total da obra (Sem mão de obra)
  3. Total da obra (Com mão de obra)
  4. O lucro da empresa é de 25% sobre o total da obra, calcule quanto a empresa receberá ao final e quanto ela deverá destinar ao custo da obra considerando o desconto da folha de pagamento.

```
fun main(){
    
    print("Digite uma largura para o terreno: ")
    val base = readln().toFloat()
    print("Digite uma altura para o terreno: ")
    val altura = readln().toFloat()
    print("Quantos quartos possuem súite no terreno?: ")
    val suite = readln().toInt()
    print("Quantos quartos NÃO possuem súite no terreno?: ")
    val quarto = readln().toInt()
    print("O terreno possui uma área de serviço?: ")
    val servico = readln().toInt()
    print("Quantos banheiros possui no terreno?: ")
    val banheiro = readln().toInt()
    print("O terreno possui piscina?: ")
    val piscina = readln().toInt()
    
    println("-------------")
    
    var mestre = 0
    
    val resultado = calculo(base, altura)
    
    println("A area do seu terreno é de: $resultado")
    
    var precoTotal = (resultado / 10).toInt() * 4500
    
    if (quarto >= 1){
         precoTotal += quarto * 12000
    }   
    if (servico >= 1){
         precoTotal += servico * 15000
    }
    if (piscina >= 1){
         precoTotal += piscina * 27550
    }
    if (suite >= 1){
         precoTotal += suite * 17000
    }
    if (banheiro >= 1){
         precoTotal += banheiro * 15000
    }
    
    
    
    println("-------------")
    
    
    if (resultado >= 10){
        mestre = 1
        println("Necessita de um Mestre da obra.")
    } else {
        println("Não necessita de um Mestre da obra")
    }
    println("-------------")
    
    var serventes = (resultado / 10).toInt()*2
    
    if (resultado >= 10){
        serventes
        println("Necessita de $serventes serventes")
    } else {
        println("Não necessita de serventes")
    }
    
    println("-------------")
    
    var engenheiro = (resultado / 100).toInt()
    
    if (resultado >= 100){
        engenheiro
        println("Necessita de $engenheiro engenheiro")
    } else {
        println("Não necessita de engenheiro")
    }
    
    println("-------------")
    
    var custoMaoDeObra = mestre * 3500
    
    if(serventes >= 1){
        custoMaoDeObra += serventes * 1900
    }
    if(engenheiro >= 1){
        custoMaoDeObra += engenheiro * 11000
    }
    
    val totalFinal = custoMaoDeObra + precoTotal
    
    val lucro = totalFinal * 0.25
    
    val custoFinal = lucro - totalFinal
    
    
   
    
    println("-------------")
    
    println("O custo do quarto sem suite é de: R$ ${suite * 12000}")
    
    println("-------------")
    
    println("O custo da área de serviço é de: R$ ${servico * 15000}")
    
    println("-------------")
    
    println("O custo da piscina é de: R$ ${piscina * 27500}")
    
    println("-------------")
    
    println("O custo do quarto com suite é de: R$ ${quarto * 17000}")
    
    println("-------------")
    
    println("O custo do banheiro é de: R$ ${banheiro * 5000}")
    
    println("-------------")
    
    println("O custo da Mao de obra vai ser: $custoMaoDeObra")
    
    println("-------------")
    
    println("O total da obra deu(Apenas a Construção): R$ $precoTotal")
    
    println("-------------")
    
    println("O valor total da obra (Construção + Mão de obra) é: R$ $totaFinal")
    
    println("-------------")
    
    println("O lucro da empresa foi de: R$ $lucro")
    
    println("-------------")
    
    println("O custo FINAL da obra seria: R$ $custoFinal")
    
    println("-------------")
}


fun calculo(base: Float, altura: Float): Float{
    return base * altura
    
}
```
