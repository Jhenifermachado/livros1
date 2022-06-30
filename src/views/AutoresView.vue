<script>
import { v4 as uuidv4} from "uuid";
export default {
    data () {
        return {
            autores: [
                { id: "0888117a-25c4-40b0-b96c-0daeb8c946fb",
                  nome: "Stephen King",
                },
            ],
            novo_autor: "",
        };
    },
methods: {
    salvar () {
        if (this.novo_autor !=="") {
            const novo_id = uuidv4 ();
            this.autores.push ({
                id: novo_id,
                nome: this.novo_autor,
            });
        }
    },
    excluir(autor){
        const indice = this.autores.index0f(autor);
        this.autores.splice(indice, 1);
    },
  },
};