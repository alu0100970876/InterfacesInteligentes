# InformeDelegados
Para esta practica hemos comnezado amodelar el mapa de la mazmorra asi como a;adir los delegados que se nos solicito 

El código empleado con los delegados es el siguiente:
 ```csharp
 #---------------------En el Game controler:
 public delegate void TipoB();
    public static event TipoB OnCambio;

	public void Start(){
		PLayer.OnAction += aumentar;
	}

	void aumentar(int var){
		PLayer.poder += var;
		if (var == -1) {
            OnCambio();
			}
		}
    
  #--------------------En el Jugador 
  public delegate void Action(int var);
	public static event Action OnAction;

	private void OnCollisionEnter(Collision collision){
		if (collision.gameObject.tag == "Tipo_A")
			OnAction (1);
		if (collision.gameObject.tag == "Tipo_B")
			OnAction (-1);
		Debug.Log ("Poder: " + poder);
	}
  
  #------------------ En los objetos tipo b
  void Start () {
        GameController.OnCambio += this.colision;
	}

    void colision() {
        Color col = new Color(Random.value, Random.value, Random.value);
        this.GetComponent<Renderer>().material.color = col;
    }
 ```
 
 ![Video demo](ezgif-6-715560838218.gifezgif)
