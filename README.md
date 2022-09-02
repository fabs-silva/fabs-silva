```java
public enum DevExperience {
JUNIOR(1), MIDLEVEL(2), SENIOR(3), NINJA(4), EVANGELIST(5);
}

public enum DevRoles {
FRONTEND(1), BACKEND(2), FULLSTACK(3), DATASCIENTIST(4), OTHER(0);
}

@Entity
@Table( name = "DEVS" )
public class Dev {
    private String name;
    private String homeTown;
    private String currentLiving;
    private Integer age;
    private DevExperience experience;
    private DevRoles role;
    private String workplace;
    private Date workingSince;
    
    ▾ public Dev ...
    
    @Id
    @GeneratedValue(generator="increment")
    @GenericGenerator(name="increment", strategy = "increment")
    public Long getId() {
        return id;
    }
    
   public String getName(){ return name; }
   
   public String getHomeTown(){ return homeTown }
   
   public String getCurrentLiving(){
      return currentLiving;
   }
   
   public Integer getAge(Integer devAge){
      if(devAge < 18) { return 18; }
      
      if(devAge >= 50) { return 30; }
      
      return devAge;
   }
   
   public DevExperience getExperience(){ return experience; }
   
   public DevRole getRole(){ return devRole; }
   
   public String getWorkplace(){ return workplace; }
   
   @Temporal(TemporalType.TIMESTAMP)
   public Date getWorkingSince() { return date; }
}

protected void setUp() throws Exception {
    sessionFactory = Persistence.createEntityManagerFactory( "org.hibernate.tutorial.jpa" );
 
    EntityManager entityManager = sessionFactory.createEntityManager();
    
    entityManager.getTransaction().begin();
    entityManager.persist(
      new Dev(
        "Fabiana Silva",
        "São Paulo",
        "Brasília",
        36,      
        1, //JUNIOR
        3, //FULLSTACK
        "Banco do Brasil",
        new Date(2022, 2, 14)
      )
    );
    entityManager.getTransaction().commit();
    entityManager.close();
}
```
