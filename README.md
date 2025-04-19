<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CME - Área Suja | Quiz Completo</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background-color: #c62828;
            color: white;
            padding: 2rem;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.2);
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .game-intro {
            background-color: white;
            padding: 2rem;
            border-radius: 8px;
            margin-bottom: 2rem;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .quiz-container {
            background-color: white;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .question {
            margin-bottom: 1.5rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid #eee;
        }
        
        .options {
            display: grid;
            grid-template-columns: 1fr;
            gap: 1rem;
            margin-top: 1rem;
        }
        
        .option {
            padding: 1rem;
            background-color: #f0f0f0;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .option:hover {
            background-color: #e0e0e0;
        }
        
        .correct {
            background-color: #4caf50;
            color: white;
        }
        
        .incorrect {
            background-color: #f44336;
            color: white;
        }
        
        button {
            background-color: #c62828;
            color: white;
            border: none;
            padding: 0.8rem 1.5rem;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            margin-top: 1rem;
            transition: background-color 0.3s;
        }
        
        button:hover {
            background-color: #b71c1c;
        }
        
        .result {
            margin-top: 2rem;
            padding: 1rem;
            text-align: center;
            font-size: 1.2rem;
            display: none;
        }
        
        footer {
            text-align: center;
            padding: 2rem;
            margin-top: 2rem;
            background-color: #333;
            color: white;
        }
        
        @media (max-width: 768px) {
            .container {
                padding: 1rem;
            }
            
            header {
                padding: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>CME - Desafio da Área Suja</h1>
        <p>Quiz Completo para Enfermeiros e Técnicos</p>
    </header>
    
    <div class="container">
        <section class="game-intro">
            <h2>Teste Seu Conhecimento sobre a Área Suja do CME</h2>
            <p>Este quiz contém 10 perguntas sobre protocolos, segurança e boas práticas na Área Suja do Centro de Material e Esterilização.</p>
            <p><strong>Como jogar:</strong></p>
            <ul>
                <li>Leia cada pergunta com atenção</li>
                <li>Selecione apenas uma resposta</li>
                <li>Receba feedback imediato</li>
                <li>Pontuação final ao concluir</li>
            </ul>
            <button id="start-btn">Iniciar Quiz</button>
        </section>
        
        <section class="quiz-container" id="quiz" style="display: none;">
            <!-- As perguntas serão inseridas dinamicamente via JavaScript -->
        </section>
    </div>
    
    <footer>
        <p>© 2023 CME Educativo - Para fins de capacitação profissional</p>
    </footer>
    
    <script>
        // Banco de perguntas e respostas
        const questions = [
            {
                question: "1. Qual é o principal objetivo da Área Suja no CME?",
                options: [
                    "Armazenar materiais esterilizados",
                    "Receber, separar e limpar os materiais contaminados",
                    "Preparar kits cirúrgicos",
                    "Realizar esterilização por autoclave"
                ],
                answer: 1,
                explanation: "A Área Suja é destinada à limpeza e descontaminação inicial dos materiais antes do processamento."
            },
            {
                question: "2. Qual EPI é OBRIGATÓRIO na Área Suja?",
                options: [
                    "Avental estéril",
                    "Óculos de proteção, luvas de borracha e gorro",
                    "Máscara N95 e sapato aberto",
                    "Touca descartável sem proteção facial"
                ],
                answer: 1,
                explanation: "EPIs como óculos, luvas resistentes e gorro protegem contra respingos e aerossóis."
            },
            {
                question: "3. O que deve ser feito PRIMEIRO ao receber instrumental contaminado?",
                options: [
                    "Lavar com água corrente",
                    "Realizar pré-lavagem para evitar ressecamento de matéria orgânica",
                    "Colocar diretamente na autoclave",
                    "Deixar de molho em água quente"
                ],
                answer: 1,
                explanation: "A pré-lavagem imediata facilita a remoção de matéria orgânica antes da limpeza detalhada."
            },
            {
                question: "4. Qual solução é recomendada para limpeza de materiais termossensíveis?",
                options: [
                    "Água e sabão neutro",
                    "Glutaraldeído a 2%",
                    "Álcool 70%",
                    "Hipoclorito de sódio a 1%"
                ],
                answer: 1,
                explanation: "Glutaraldeído é eficaz para desinfecção de materiais que não suportam calor."
            },
            {
                question: "5. O descarte de perfurocortantes na Área Suja deve ser feito em:",
                options: [
                    "Saco plástico comum",
                    "Recipiente rígido e resistente",
                    "Lixeira com tampa vermelha",
                    "Caixa de papelão"
                ],
                answer: 1,
                explanation: "Recipientes rígidos previnem acidentes com perfurações."
            },
            {
                question: "6. Qual é o tempo MÁXIMO que materiais críticos podem permanecer na Área Suja antes do processamento?",
                options: [
                    "2 horas",
                    "6 horas",
                    "12 horas",
                    "24 horas"
                ],
                answer: 0,
                explanation: "O prazo de 2 horas evita a formação de biofilme bacteriano."
            },
            {
                question: "7. Sobre a limpeza manual na Área Suja, é CORRETO afirmar:",
                options: [
                    "Deve-se usar água quente para remover matéria orgânica",
                    "Escovas devem ser trocadas diariamente ou quando desgastadas",
                    "O uso de luvas de procedimento é suficiente para proteção",
                    "A secagem pode ser feita com compressas de tecido"
                ],
                answer: 1,
                explanation: "Escovas devem ser substituídas regularmente para evitar contaminação cruzada."
            },
            {
                question: "8. Qual destes NÃO deve ser processado na Área Suja?",
                options: [
                    "Instrumental cirúrgico metálico",
                    "Endoscópios flexíveis",
                    "Materiais descartáveis contaminados",
                    "Embalagens de papel grau cirúrgico"
                ],
                answer: 3,
                explanation: "Embalagens estéreis não devem entrar na Área Suja para evitar contaminação."
            },
            {
                question: "9. A desinfecção de superfícies na Área Suja deve ocorrer:",
                options: [
                    "Apenas no final do turno",
                    "Após cada procedimento e imediatamente após derramamentos",
                    "Duas vezes ao dia",
                    "Quando visivelmente sujas"
                ],
                answer: 1,
                explanation: "Limpeza imediata após uso previne acúmulo de contaminantes."
            },
            {
                question: "10. O fluxo de trabalho na Área Suja deve ser:",
                options: [
                    "Circular, permitindo retorno de materiais",
                    "Linear, sempre no sentido sujo → limpo",
                    "Aleatório, conforme necessidade",
                    "Inverso ao da Área Limpa"
                ],
                answer: 1,
                explanation: "Fluxo linear unidirecional previne contaminação cruzada."
            }
        ];

        // Variáveis do jogo
        let currentQuestion = 0;
        let score = 0;
        let quizCompleted = false;

        // Elementos DOM
        const quizContainer = document.getElementById('quiz');
        const startBtn = document.getElementById('start-btn');

        // Iniciar quiz
        startBtn.addEventListener('click', startQuiz);

        function startQuiz() {
            document.querySelector('.game-intro').style.display = 'none';
            quizContainer.style.display = 'block';
            showQuestion();
        }

        // Mostrar pergunta atual
        function showQuestion() {
            if (currentQuestion >= questions.length) {
                showResult();
                return;
            }

            const question = questions[currentQuestion];
            quizContainer.innerHTML = `
                <div class="question">
                    <h3>${question.question}</h3>
                    <div class="options">
                        ${question.options.map((option, index) => `
                            <div class="option" onclick="selectAnswer(${index})">
                                ${option}
                            </div>
                        `).join('')}
                    </div>
                </div>
                <div id="feedback" style="margin-top: 1rem; display: none;"></div>
                <button id="next-btn" style="display: none;" onclick="nextQuestion()">Próxima Pergunta</button>
            `;
        }

        // Selecionar resposta
        function selectAnswer(selectedIndex) {
            if (quizCompleted) return;

            const question = questions[currentQuestion];
            const options = document.querySelectorAll('.option');
            const feedback = document.getElementById('feedback');

            options.forEach((option, index) => {
                option.style.pointerEvents = 'none';
                if (index === question.answer) {
                    option.classList.add('correct');
                } else if (index === selectedIndex && index !== question.answer) {
                    option.classList.add('incorrect');
                }
            });

            if (selectedIndex === question.answer) {
                score++;
                feedback.innerHTML = `<p style="color: #4caf50;">✓ Correto! ${question.explanation}</p>`;
            } else {
                feedback.innerHTML = `<p style="color: #f44336;">✗ Incorreto. ${question.explanation}</p>`;
            }

            feedback.style.display = 'block';
            document.getElementById('next-btn').style.display = 'block';
        }

        // Próxima pergunta
        function nextQuestion() {
            currentQuestion++;
            if (currentQuestion < questions.length) {
                showQuestion();
            } else {
                showResult();
            }
        }

        // Mostrar resultado final
        function showResult() {
            quizCompleted = true;
            const percentage = Math.round((score / questions.length) * 100);
            
            let message;
            if (percentage >= 90) {
                message = "Excelente! Você é um especialista na Área Suja do CME!";
            } else if (percentage >= 70) {
                message = "Bom trabalho! Seu conhecimento é sólido, mas pode melhorar em alguns pontos.";
            } else if (percentage >= 50) {
                message = "Você acertou a metade. Recomendamos revisar os protocolos da Área Suja.";
            } else {
                message = "Seu conhecimento precisa ser reforçado. Consulte os manuais do CME e treine novamente.";
            }

            quizContainer.innerHTML = `
                <div class="result">
                    <h3>Quiz Concluído!</h3>
                    <p>Você acertou ${score} de ${questions.length} perguntas (${percentage}%)</p>
                    <p><strong>${message}</strong></p>
                    <button onclick="restartQuiz()">Refazer Quiz</button>
                </div>
            `;
        }

        // Reiniciar quiz
        function restartQuiz() {
            currentQuestion = 0;
            score = 0;
            quizCompleted = false;
            showQuestion();
        }

        // Tornar funções acessíveis globalmente
        window.selectAnswer = selectAnswer;
        window.nextQuestion = nextQuestion;
        window.restartQuiz = restartQuiz;
    </script>
</body>
</html>
