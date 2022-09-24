# choropleth-map-
import chart_studio.plotly as py
import plotly.graph_objs as go
import pandas as pd
from plotly.offline import download_plotlyjs,init_notebook_mode,plot,iplot
init_notebook_mode(connected=True)
df=pd.read_csv('2011_US_AGRI_Exports')
df.head() 
data = dict(type='choropleth',
           locations=df['code'],
           locationmode='USA-states',
           colorscale='YlOrRd',
           text=df['text'],
           z=df['total exports'],
           marker=dict(line=dict(color='rgb(0,0,0)',width=2)),
           colorbar={'title':'Millions USD'}
           )
layout= dict(title='USA exports in 2011',
            geo=dict(scope='usa',showlakes=True, lakecolor='rgb(85,190,240)'))
choromap2=go.Figure(data=[data],layout=layout)
iplot(choromap2)
