# Paquetes
Microsoft.EntityFrameworkCore.SqlServer
Microsoft.EntityFrameworkCore.Tools

# automapper 
AutoMapper

# without automapper
public IActionResult GetAllStudents()
{
    var students = studentRepository.GetStudents();

    var domainModelStudents = new List<Student>();

    foreach(var student in students)
    {
        domainModelStudents.Add(new Student
        {
            Id = student.Id,
            FirstName = student.FirstName,
            LastName = student.LastName,
            DateOfBirth = student.DateOfBirth,
            Email = student.Email,
            Mobile = student.Mobile,
            ProfileImageUrl = student.ProfileImageUrl,
            GenderId = student.GenderId,
            Address = new Address()
            {
                Id = student.Address.Id,
                PhysicalAddress = student.Address.PhysicalAddress,
                PostalAddress = student.Address.PostalAddress
            },
            Gender = new Gender()
            { 
                Id = student.Gender.Id,
                Description = student.Gender.Description
            }
        });
    }

    return Ok(domainModelStudents);
}