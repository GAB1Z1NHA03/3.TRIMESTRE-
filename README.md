<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Relatório de Faltas - Arthur</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f7fc;
            padding: 20px;
        }

        .container {
            max-width: 800px;
            margin: auto;
            padding: 20px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        .header {
            text-align: center;
            margin-bottom: 30px;
        }

        h1 {
            color: #333;
        }

        .grafico {
            margin-top: 40px;
        }

        .tabela {
            margin-top: 20px;
            width: 100%;
            border-collapse: collapse;
        }

        .tabela th, .tabela td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: center;
        }

        .tabela th {
            background-color: #f2f2f2;
        }

        .grafico {
            width: 100%;
            height: 300px;
        }
    </style>
</head>
<body>

    <div class="container">
        <div class="header">
            <h1>Relatório de Faltas - Arthur</h1>
            <p>Relatório das presenças e faltas de Arthur no semestre.</p>
        </div>

        <div class="grafico">
            <canvas id="graficoFaltas"></canvas>
        </div>

        <table class="tabela">
            <thead>
                <tr>
                    <th>Disciplina</th>
                    <th>Presenças</th>
                    <th>Faltas</th>
                    <th>Total de Aulas</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Matemática</td>
                    <td>18</td>
                    <td>2</td>
                    <td>20</td>
                </tr>
                <tr>
                    <td>Português</td>
                    <td>16</td>
                    <td>4</td>
                    <td>20</td>
                </tr>
                <tr>
                    <td>História</td>
                    <td>19</td>
                    <td>1</td>
                    <td>20</td>
                </tr>
                <tr>
                    <td>Ciências</td>
                    <td>17</td>
                    <td>3</td>
                    <td>20</td>
                </tr>
            </tbody>
        </table>
    </div>

    <script>
        // Dados para o gráfico
        const data = {
            labels: ['Matemática', 'Português', 'História', 'Ciências'],
            datasets: [{
                label: 'Presenças',
                data: [18, 16, 19, 17],
                backgroundColor: 'rgba(54, 162, 235, 0.6)',
                borderColor: 'rgba(54, 162, 235, 1)',
                borderWidth: 1
            },
            {
                label: 'Faltas',
                data: [2, 4, 1, 3],
                backgroundColor: 'rgba(255, 99, 132, 0.6)',
                borderColor: 'rgba(255, 99, 132, 1)',
                borderWidth: 1
            }]
        };

        // Configuração do gráfico
        const config = {
            type: 'bar',
            data: data,
            options: {
                responsive: true,
                plugins: {
                    legend: {
                        position: 'top',
                    },
                    tooltip: {
                        callbacks: {
                            label: function(tooltipItem) {
                                return tooltipItem.dataset.label + ': ' + tooltipItem.raw;
                            }
                        }
                    }
                },
                scales: {
                    x: {
                        beginAtZero: true
                    },
                    y: {
                        beginAtZero: true,
                        title: {
                            display: true,
                            text: 'Número de Aulas'
                        }
                    }
                }
            }
        };

        // Renderizando o gráfico
        const ctx = document.getElementById('graficoFaltas').getContext('2d');
        new Chart(ctx, config);
    </script>

</body>
</html>
