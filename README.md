```java
public enum DevExperience { JUNIOR(1), MIDLEVEL(2), SENIOR(3), NINJA(4), EVANGELIST(5); }

public enum DevRoles { FRONTEND(1), BACKEND(2), FULLSTACK(3), DATASCIENTIST(4), OTHER(0); }

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
    
    ▾ //GETTERS ...
    
   public Integer getAge(Integer devAge){
      if(devAge < 18) { return 18; }
      
      if(devAge >= 50) { return 30; }
      
      return devAge;
   }
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
