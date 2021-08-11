# testecarrefour3


/**************************************************************************
Desafio
Há um país denominado Lolipad, todos os habitantes ficam felizes em pagar seus impostos, pois sabem que nele não existem políticos corruptos e os recursos arrecadados são utilizados em benefício da população, sem qualquer desvio. A moeda deste país é o Loli, cujo símbolo é o R$.

Você terá o desafio de ler um valor com duas casas decimais, equivalente ao salário de uma pessoa de Loli. Em seguida, calcule e mostre o valor que esta pessoa deve pagar de Imposto de Renda, segundo a tabela abaixo.



Lembre que, se o salário for R$ 3002.00, a taxa que incide é de 8% apenas sobre R$ 1000.00, pois a faixa de salário que fica de R$ 0.00 até R$ 2000.00 é isenta de Imposto de Renda. No exemplo fornecido (abaixo), a taxa é de 8% sobre R$ 1000.00 + 18% sobre R$ 2.00, o que resulta em R$ 80.36 no total. O valor deve ser impresso com duas casas decimais.

Entrada
A entrada contém apenas um valor de ponto flutuante, com duas casas decimais.

Saída
Imprima o texto "R$" seguido de um espaço e do valor total devido de Imposto de Renda, com duas casas após o ponto. Se o valor de entrada for menor ou igual a 2000, deverá ser impressa a mensagem "Isento".

 
Exemplos de Entrada	Exemplos de Saída
3002.00

R$ 80.36

1701.12

Isento

4520.00

R$ 355.60

******************************************************************/


fun main(args: Array<String>) 
{
  fun Double.format(digits: Int) = "%.${digits}f".format(this).replace(',', '.')

  val valor = readLine()!!.toDouble()
  var imposto = 0.0
  var diferenca: Double

  if (valor > 4500) {
    imposto = 1000 * 0.08 + 1500 * 0.18
    diferenca = valor - 4500
    imposto += diferenca * 0.28
  } else if (valor > 3000) {
    imposto = 1000 * 0.08
    diferenca = valor - 3000
    imposto += diferenca * 0.18
  } else if (valor > 2000) {
    diferenca = valor - 2000
    imposto = diferenca * 0.08
  }
  
  if (imposto == 0.0) println("Isento") else println("R$ ${imposto.format(2)}")
}
