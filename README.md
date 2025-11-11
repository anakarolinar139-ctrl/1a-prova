def calcular_media(notas):
    return sum(notas) / len(notas)

def situacao_final(media_anual):
    if media_anual >= 48:
        return "Aprovado ✅"
    elif 40 <= media_anual < 48:
        return "Recuperação ⚠️"
    else:
        return "Reprovado ❌"

def sistema_escolar():
    print("=== SISTEMA ESCOLAR ===\n")
    nome = input("Digite o nome do aluno: ")

    notas = []
    for i in range(1, 10):
        while True:
            try:
                nota = float(input(f"Digite a nota {i} (0 a 100): "))
                if 0 <= nota <= 100:
                    notas.append(nota)
                    break
                else:
                    print("⚠️ Nota deve estar entre 0 e 100.")
            except ValueError:
                print("⚠️ Digite um número válido.")

    # Dividindo em trimestres (3 notas cada)
    trimestre1 = notas[0:3]
    trimestre2 = notas[3:6]
    trimestre3 = notas[6:9]

    media1 = calcular_media(trimestre1)
    media2 = calcular_media(trimestre2)
    media3 = calcular_media(trimestre3)

    print("\n=== MÉDIAS POR TRIMESTRE ===")
    print(f"1º Trimestre: {media1:.2f}")
    print(f"2º Trimestre: {media2:.2f}")
    print(f"3º Trimestre: {media3:.2f}")

    # Calculando médias semestrais
    semestre1 = calcular_media([media1, media2])
    semestre2 = media3  # último trimestre corresponde ao 2º semestre

    print("\n=== MÉDIAS POR SEMESTRE ===")
    print(f"1º Semestre: {semestre1:.2f}")
    print(f"2º Semestre: {semestre2:.2f}")

    # Média final (dos dois semestres)
    media_final = calcular_media([semestre1, semestre2])
    print(f"\nMÉDIA FINAL: {media_final:.2f}")

    # Situação final
    print(f"\nSituação de {nome}: {situacao_final(media_final)}")

# Executa o sistema
sistema_escolar()
