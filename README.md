EVALUATE SUMMARIZECOLUMNS('Components'[Component Layer Name], 'Quality Risks'[Quality Risk ID], 'Quality Risks'[Home Component Layer ID],'Controls'[Response Type])

EVALUATE
CALCULATETABLE(
    SUMMARIZECOLUMNS(
        'Components'[Component Layer Name],
        'Components'[Component Layer ID],
        'Controls'[Response Type]
    ),
    KEEPFILTERS( TREATAS( { @ComponentParam },  'Components'[Component Layer ID] ) ),
    KEEPFILTERS( TREATAS( { @ComponentParam2 }, 'Controls'[Response Type] ) )
)
ORDER BY 'Components'[Component Layer Name], 'Controls'[Response Type]


EVALUATE SUMMARIZECOLUMNS('QO To QR Responses: QualityRisks Unpivoted'[Component], 'QO To QR Responses: QualityRisks Unpivoted'[Quality Risk ID], 'QO To QR Responses: QualityRisks Unpivoted'[Attribute], 'QO To QR Responses: QualityRisks Unpivoted'[Value],'Controls'[Response Type])


EVALUATE SUMMARIZECOLUMNS('QO To QR Responses: QualityRisks'[Component], 'QO To QR Responses: QualityRisks'[Quality Risk ID], 'QO To QR Responses: QualityRisks'[What other risk assessment consideration were evaluated in whether, how, and the degree to which the achievement of the quality objectives may be adversely affected by the risks and related responses (e.g., items deemed to be of low or no risk, parts of a process with very limited occurrence, or scoping of ranks or service lines)?  If yes, please describe.],'Controls'[Response Type])

EVALUATE
SUMMARIZECOLUMNS(
    'Components'[Component Layer ID],
    'Components'[Component Layer Name]
)
ORDER BY 'Components'[Component Layer Name]

EVALUATE
SUMMARIZECOLUMNS(
    'Controls'[Response Type],
    KEEPFILTERS( TREATAS( @ComponentParam , 'Components'[Component Layer ID] ) )
)
ORDER BY 'Controls'[Response Type]
