- 👋 Hi, I’m @Zeredtx
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Zeredtx/Zeredtx is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from flask import Flask, request, jsonify

app = Flask(__name__)

# Dicionário para armazenar as APIs
apis = {}

# Rota para adicionar uma nova API
@app.route('/adicionar_api', methods=['POST'])
def adicionar_api():
    data = request.get_json()
    nome_api = data['nome']
    url_api = data['url']
    apis[nome_api] = url_api
    return jsonify({'mensagem': 'API adicionada com sucesso'})

# Rota para listar todas as APIs disponíveis
@app.route('/listar_apis', methods=['GET'])
def listar_apis():
    return jsonify(apis)

if __name__ == '__main__':
    app.run(debug=True)
    
