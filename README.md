# 🍷 Predição da Qualidade de Vinhos com Random Forest

Este projeto aplica o algoritmo **Random Forest** para prever a qualidade de vinhos tintos com base em suas características físico-químicas.  
A base utilizada é o **Wine Quality Dataset (red wine)**, amplamente usado em estudos de machine learning.

---

##  Objetivo
- Prever a **pontuação de qualidade dos vinhos** (variável `Qualidade`) em uma classificação multiclass.
- Explorar como diferentes atributos químicos influenciam a qualidade.
- Avaliar o impacto do **desbalanceamento de dados** e aplicar técnicas para melhorar a previsão das classes minoritárias.

---

##  Etapas do Projeto
1. **Pré-processamento**
   - Verificação de tipos de dados e valores faltantes.
   - Análise descritiva e identificação de outliers.
   - Estudo da distribuição da variável alvo (Qualidade).

2. **Análise exploratória**
   - Correlação entre variáveis e a qualidade.
   - Seleção das variáveis mais relevantes: `Álcool`, `Densidade`, `Acidez volátil`, `Sulfatos`, `Ácido cítrico`.

3. **Modelagem inicial**
   - Treinamento de um modelo **Random Forest**.
   - Avaliação com métricas de classificação e matriz de confusão.
   - Identificação da dificuldade em prever classes raras (3, 4, 8).

4. **Otimização de hiperparâmetros**
   - Uso de **RandomizedSearchCV** para ajustar parâmetros como `n_estimators`, `max_depth`, `min_samples_split` e `min_samples_leaf`.

5. **Técnicas de balanceamento**
   - **Class Weights**: ajuste automático da importância das classes minoritárias.
   - **SMOTE (Oversampling)**: geração de exemplos sintéticos para classes raras.
   - **Combinação SMOTE + Class Weights**: abordagem híbrida que trouxe maior equilíbrio entre todas as classes.

---

## Resultados
- **Modelo inicial**: acurácia ≈ 64%, mas F1-score nulo para classes raras.  
- **Após Random Search**: melhora nas classes centrais, mas raras ainda ignoradas.  
- **SMOTE + Class Weights**:
  - Macro F1-score subiu de **0.30 → 0.42** (+40%).  
  - Classes 4, 7 e 8 passaram a ser reconhecidas.  
  - Acurácia geral ≈ 62% (leve queda, mas compensada pelo ganho em equilíbrio).  

---

##  Conclusão
O estudo demonstrou que ajustes de hiperparâmetros não são suficientes em cenários de **desbalanceamento severo**.  
A combinação de **SMOTE + class_weight** mostrou-se a estratégia mais eficaz, tornando o modelo mais justo e representativo, com melhor desempenho nas classes minoritárias.  

---

## Tecnologias utilizadas
- Python 3.x  
- Pandas, NumPy  
- Scikit-learn  
- Imbalanced-learn  
- Matplotlib, Seaborn  

---

##  Estrutura do projeto
- `winequality-red.csv` → dataset original.  
- `wine_corr.csv` → dataset reduzido com variáveis mais correlacionadas.  
- `notebook.ipynb` → código completo com análises, modelagem e resultados.  
- `README.md` → documentação do projeto.  

---

##  Próximos passos
- Testar outros algoritmos (XGBoost, LightGBM).  
- Aplicar técnicas avançadas de **ensemble** para classes raras.  
- Explorar **data augmentation** ou agrupamento de classes muito raras (ex.: 3 e 4).  

---

## Autoria  
Projeto desenvolvido por **Maria Santos**, como parte da atividade do curso **Ciências de Dados - EBAC - Módulo 32**.

