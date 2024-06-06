# Descrição da Solução

        O principal problema trazido foi a lentidão de consultas no aplicativo devido aos dados estarem em bancos de dados legados. Como os bancos são desatualizados, eles demoram para responder e tem menos escalabilidadade e resistência à falhas.
        Uma ideia inicial seria passar os dados dos bancos legados para a nuvem, que contêm bases de dados mais modernas. No entanto, o parceiro apontou que essa ideia poderia ser muito custosa, sendo assim menos prática.
        Com isso, foi pensada uma alternativa que apresentasse benefícios análogos, mas um custo menor. A solução envolve colocar um "snapshot" do banco na nuvem, que seria atualizado a cada 5 minutos, uma espécie de cache. Isso reduziria o custo pois operações de write só seriam realizadas a cada 5 minutos, enquanto, caso o banco principal fosse colocado na nuvem, haveriam operações write a cada segundo.
        Essa solução apresenta um tradeoff, o fato de que o cliente poderia receber informações que apresentassem um atraso de até 5 minutos, enquanto hoje ele recebe as informações em tempo real, mesmo que elas possam demorar alguns segundos para chegar até ele. A ideia pensada para combater o lado negativo desse tradeoff é a presença de um botão de atualizar, que, quando clicado, busca direto no banco legado, o que demoraria mais, mas ainda assim seria mais rápido do que é hoje, já que esse estaria menos sobrecarrecado.
        Com isso, a solução proposta busca reduzir o período de latência das consultas enquanto mantêm o custo total o menor possível.