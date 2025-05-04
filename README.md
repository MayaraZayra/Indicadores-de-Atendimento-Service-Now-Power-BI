# Indicadores-de-Atendimento-Service-Now-Power-BI

Média de CH Abertos por Ano = 
AVERAGEX(VALUES('dCalendário'[Mês/Ano]),
[TT CH Abertos])

Média de TT Em aberto por Ano = 
AVERAGEX(
	KEEPFILTERS(VALUES('dCalendário'[Ano])),
	CALCULATE([TT Em aberto])
)

Média de TT Encerrados SLA = 
AVERAGEX(VALUES('dCalendário'[Mês/Ano]),
[TT SLA])

% Promotores = 
CALCULATE([TT CH Avaliados], 'fPesquisa de Satisfação'[Valor] IN { 10, 9 })/[TT CH Avaliados]

% Detratores = 
CALCULATE(
	[TT CH Avaliados],
	'fPesquisa de Satisfação'[Valor] IN { 1, 2, 3, 4, 5, 6 }
)/[TT CH Avaliados]

NPS = ([% Promotores]-[% Detratores])*100
