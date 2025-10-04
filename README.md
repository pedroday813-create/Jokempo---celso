# Jokempo---celso   

import java.util.Scanner;
import java.util.Random;

public class Jokenpo {

    public static void main(String[] args) {
        // Inicializa o Scanner para ler a entrada do usuário e o Random para a escolha da máquina.
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        // Array com as opções para facilitar a exibição do texto
        String[] opcoes = {"Pedra", "Papel", "Tesoura"};

        System.out.println("=== Bem-vindo ao Jokenpô! ===");

        // Loop principal do jogo, continua enquanto o jogador quiser jogar novamente.
        while (true) {
            System.out.println("\nEscolha sua jogada:");
            System.out.println("1 - Pedra");
            System.out.println("2 - Papel");
            System.out.println("3 - Tesoura");
            System.out.print("Sua escolha: ");

            // --- Etapa 1: Obter a escolha do usuário ---
            int escolhaUsuario = -1;
            // Validação para garantir que o usuário digite um número entre 1 e 3
            while (escolhaUsuario < 1 || escolhaUsuario > 3) {
                if (!scanner.hasNextInt()) { // Verifica se a entrada não é um número
                    System.out.println("Entrada inválida. Por favor, digite um número (1, 2 ou 3).");
                    scanner.next(); // Limpa o buffer do scanner
                    System.out.print("Sua escolha: ");
                    continue;
                }
                escolhaUsuario = scanner.nextInt();
                if (escolhaUsuario < 1 || escolhaUsuario > 3) {
                    System.out.println("Opção inválida. Escolha entre 1, 2 ou 3.");
                    System.out.print("Sua escolha: ");
                }
            }

            // --- Etapa 2: Gerar a escolha da máquina ---
            // random.nextInt(3) gera um número aleatório: 0, 1 ou 2.
            int escolhaMaquina = random.nextInt(3);

            // Ajusta a escolha do usuário para o índice do array (0, 1, 2)
            int indiceUsuario = escolhaUsuario - 1;

            // --- Etapa 3: Exibir as escolhas ---
            System.out.println("\n------------------------------------");
            System.out.println("Você escolheu: " + opcoes[indiceUsuario]);
            System.out.println("A máquina escolheu: " + opcoes[escolhaMaquina]);
            System.out.println("------------------------------------");


            // --- Etapa 4: Determinar e exibir o resultado ---
            if (indiceUsuario == escolhaMaquina) {
                System.out.println("Resultado: Deu EMPATE!");
            } else if ((indiceUsuario == 0 && escolhaMaquina == 2) || // Pedra ganha de Tesoura
                       (indiceUsuario == 1 && escolhaMaquina == 0) || // Papel ganha de Pedra
                       (indiceUsuario == 2 && escolhaMaquina == 1)) { // Tesoura ganha de Papel
                System.out.println("Resultado: PARABÉNS! Você ganhou!");
            } else {
                System.out.println("Resultado: Que pena! Você não ganhou desta vez.");
            }
            
            // --- Etapa 5: Perguntar se quer jogar novamente ---
            System.out.print("\nDeseja jogar novamente? (s/n): ");
            String jogarNovamente = scanner.next();

            // Se a resposta não for "s" (ignorando maiúsculas/minúsculas), o loop para.
            if (!jogarNovamente.equalsIgnoreCase("s")) {
                break;
            }
        }
        
        System.out.println("\nObrigado por jogar! Até a próxima.");
        scanner.close(); // Fecha o scanner para liberar recursos.
    }
}
